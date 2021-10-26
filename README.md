# Hobbie Mobile App
Create, share, and discover collections of rare or noteworthy possessions<br/>
## Table of Contents
&nbsp; &nbsp;1. [Project Overview](#overview)
<br/>
&nbsp; &nbsp;2. [Reusable Component Demo](#demo)
<br/>
&nbsp; &nbsp;3. [Final Thoughts](#finalthoughts)
<a name="overview"/>
## Project Overview
Welcome! First off, thank you for taking the time to view this project. This repository will describe and show the features of my Hobbie mobile app. It was created using React Native, which makes it compatible with both iOS and Android devices.

There are four major features of the app aside from the user authentication. The first of which allows the user to catalog and view their personal collections. Items can be added or removed as the user builds their physical collection. These collections are then displayed in a stack layout which the user can swipe through. The user can also manage their profile from this screen.

Secondly, the user can explore new items from the community database. This screen features a grid of images that can be viewed and expanded. A list of filters at the top of the screen allows the user to select what type of item is displayed. Anything from comic books to model trains can be selected. The user can also look for other members or groups using the search bar component at the top.

Next, a map feature was implemented allowing the user to locate nearby auction houses, yard sales, hobby stores, and flea markets. The type of locations displayed can be selected using a list of pressable filters. Alternatively, a search bar can be used to find a specific business or location. These features are actually reusable functional components used in the discover screen as well. Further discussion about these reusable components can be found in the following section - [Reusable Component Demo](#demo)

The final feature is an activity feed that displays events from the user's own usage or any accounts the user has followed. This includes any new additions to a collection, item trades, locations visited, and milestones reached.

For image captions, point out behavior. For example, “As the user scrolls, the search bar is hidden or displayed, depending on the direction.”
The images below are screenshots of the map, discover, and home screen<br/>
<br/>
![MapScreen](https://johndan2354.github.io/BBMobileImages/Map.PNG) &nbsp; &nbsp; &nbsp; &nbsp; &nbsp; ![ComicsScreen](https://johndan2354.github.io/BBMobileImages/Comics.PNG)
<a name="demo"/>
## Reusable Component Demo
Makes use of a given list of categories to render selectable buttons. A reusable component is imported which can be used in other screens. With the useState hook, state variables can be used without the need for a class component.
```javascript
// App.js
import React, { useState } from 'react';
import { FlatList } from 'react-native';

import { data } from '../data';
import ListFilters from '../components/ListFilters';

const App = () => {
  // Holds the unique identifier of the selected button
  const [selected, setSelected] = useState('1');

  const renderList = ({ item }) => {
    // If the current item in the list is selected then text color is set to 'red'
    const textColor = item.id === selected ? 'red' : 'gray';
    return (
      <ListFilters 
        category={item.title}
        textColor={textColor}
        onPress={() => setSelected(item.id)}
      />
    );
  };

  return (
    <FlatList
      horizontal={true}
      data={data}
      renderItem={renderList}
      keyExtractor={(item) => item.id}
    />
  );
};
```
Each item in the list is passed to this component where it is rendered and formatted. Depending on what button is selected, the color of the text will change to red. The component receives this data as props.
```javascript
// ListFilters.js
import React from 'react';
import { Text, TouchableOpacity } from 'react-native';

const ListFilters = (props) => {
  return (
    <TouchableOpacity onPress={props.onPress}>
      <Text style={{color: props.textColor}}>
        {props.category}
      </Text>
    </TouchableOpacity>
  );
};

export default ListFilters;
```

<a name="finalthoughts"/>

## Final Thoughts
Since this was an independent project I took on many different roles in the development process. It was up to me to gather requirements and to select the tools needed. A lot of time went into the design and creating detailed mockups. This is crucial for the implementation phase when the focus should be on writing good code, not on how the app should look.<br/>
<br/>
During development real mobile devices were used, including the iPhone 8, X, 13, and a Samsung tablet. This allowed me to program the behavior of the app more effectively. There are obvious challenges that arise when dealing with a cross-platform framework. Support for certain properties or features will vary and may not work as intended. It was also difficult sizing the app appropriately for the various screen dimensions.<br/>
<br/>
Many new features were added to React when I first started this project. React Hooks were new to me at the time. These Hooks include useState, useEffect, and useRef. All of which are implemented in the project. I found the use of Hooks to be a great addition to React. My code is more efficient and looks cleaner than the equivalent class component. Other skills gained from this project include animations and Redux for state management. I familiarized myself with a handful of animation libraries so I could implement a hideable header and a search bar that can shrink/expand. The second tool, Redux, was very useful in the user authentication feature. Redux made it possible to store login data for use in other components that otherwise would not have a safe and reliable way to access said data.<br/>
