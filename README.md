# PRINCE-NYANGASYA-MAST5112-POE
POE FOR MOBILE APP SCRIPTING

import React, { useState } from 'react';
import { View, TextInput, Button, Text, StyleSheet, ScrollView, FlatList } from 'react-native';


const randomDishes = [
  // (You.com, 2024)
  { id: '1', name: 'Spaghetti Carbonara', course: 'Main', price: 129.99 , },
  { id: '2', name: 'Caesar Salad', course: 'Starter', price: 69.99 },
  { id: '3', name: 'Ice Cream', course: 'Dessert', price: 29.99 },
  { id: '4', name: 'Beef Alfredo', course: 'Main', price: 199.99 },
  { id: '5', name: 'Tomato Soup', course: 'Starter', price: 61.49 },
  { id: '6', name: 'Chocolate cake', course: 'Dessert', price: 95.50 },
];

const ChefApp = () => {
  const [dishName, setDishName] = useState('');
  const [description, setDescription] = useState('');
  const [course, setCourse] = useState('');
  const [price, setPrice] = useState('');
  const [summary, setSummary] = useState('');
  const [dishCount, setDishCount] = useState(0); // Counter for dishes

  const handleSubmit = () => {
    const summaryText = `Dish: ${dishName}\nDescription: ${description}\nCourse: ${course}\nPrice: R${price}`;
    setSummary(summaryText);
    setDishCount(dishCount + 1);
  };

  const renderRandomDish = ({ item }) => (
    <View style={styles.randomDishContainer}>
      <Text style={styles.randomDishName}>{item.name}</Text>
      <Text>{item.course} - R{item.price.toFixed(2)}</Text>
    </View>
  );

  return (
    // The IIE (2024)
    <ScrollView contentContainerStyle={styles.container}> 
      <Text style={styles.header}>Chef Christoffel</Text>

      <Text style={styles.menuHeader}>Menu</Text>
      <FlatList
        horizontal
        data={randomDishes}
        renderItem={renderRandomDish}
        keyExtractor={item => item.id}
        showsHorizontalScrollIndicator={false}
        contentContainerStyle={styles.randomMenu}
      />

      <TextInput
        style={styles.input}
        placeholder="Dish Name"
        value={dishName}
        onChangeText={setDishName}
      />

      <TextInput
        style={styles.input}
        placeholder="Description"
        value={description}
        onChangeText={setDescription}
      />

      <TextInput
        style={styles.input}
        placeholder="Course (e.g., Starter, Main, Dessert)"
        value={course}
        onChangeText={setCourse}
      />

      <TextInput
        style={styles.input}
        placeholder="Price"
        value={price}
        onChangeText={setPrice}
        keyboardType="numeric"
      />
      <Text style={styles.counterText}>Dishes Prepared: {dishCount}</Text>
      <Button title="Submit" onPress={handleSubmit}/>

      {summary ? (
        <View style={styles.summaryContainer}>
          <Text style={styles.summaryHeader}>Dish Summary</Text>
          <Text style={styles.summaryText}>{summary}</Text>
        </View>
      ) : null}
    </ScrollView>
  );
};




const styles = StyleSheet.create({
  container: {
    flexGrow: 1,
    padding: 20,
    justifyContent: 'center',
    backgroundColor: '#e0f7fa',
  },
  header: {
    fontSize: 24,
    fontWeight: 'bold',
    marginBottom: 20,
    textAlign: 'center',
  },
  menuHeader: {
    fontSize: 18,
    fontWeight: 'bold',
    marginBottom: 10,
    textAlign: 'center',
  },
  randomMenu: {
    paddingVertical: 10,
    marginBottom: 10,
  },
  randomDishContainer: {
    padding: 10,
    backgroundColor: '#f0f4f8',
    borderRadius: 5,
    marginRight: 10,
    borderWidth: 1,
    borderColor: 'black',
  },
  randomDishName: {
    fontSize: 16,
    fontWeight: 'bold',
  },
  input: {
    height: 40,
    borderColor: 'black',
    borderWidth: 1,
    marginBottom: 20,
    paddingHorizontal: 10,
    borderRadius: 5,
  },
  summaryContainer: {
    marginTop: 20,
    padding: 10,
    backgroundColor: '#f9f9f9',
    borderRadius: 5,
    borderWidth: 1,
    borderColor: 'black',
  },
  summaryHeader: {
    fontSize: 18,
    fontWeight: 'bold',
    marginBottom: 10,
  },
  summaryText: {
    fontSize: 16,
    lineHeight: 24,
  },
});

export default ChefApp;

//Reference List
//The IIE. 2024. Mobile App Scripting [MAST5112 d/p/w MODULE MANUAL 2024]. The Independent Institute of Education: Unpublished.
//You.com. 2024. You.com Smart Assistant. [Large language model]. Available at: https://www.you.com [Accessed: 3 October 2024].
