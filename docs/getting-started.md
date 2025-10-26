import React, { useState } from 'react';
import { View, FlatList, Text, StyleSheet, SafeAreaView } from 'react-native';
// 1. تم تعديل الـ import لإضافة Avatar
import { ListItem, Avatar } from 'react-native-elements';

// 2. تم تعديل البيانات لإضافة رابط صورة
const MOCK_DESTINATIONS = [
  {
    id: '1',
    name: 'Marrakech',
    description: 'The Red City, famous for its souks.',
    image: 'https://images.unsplash.com/photo-1559922080-601443425f38?q=80&w=2070&auto=format&fit=crop',
  },
  {
    id: '2',
    name: 'Fes',
    description: 'Home to the oldest university.',
    image: 'https://images.unsplash.com/photo-1563810266067-c0e9fec3f804?q=80&w=1974&auto=format&fit=crop',
  },
  {
    id: '3',
    name: 'Chefchaouen',
    description: 'The Blue Pearl of Morocco.',
    image: 'https://images.unsplash.com/photo-1547990145-3d8b13f1604a?q=80&w=1966&auto=format&fit=crop',
  },
  {
    id: '4',
    name: 'Sahara Desert',
    description: 'Experience the vast dunes.',
    image: 'https://images.unsplash.com/photo-1519973800259-a3c393822185?q=80&w=2070&auto=format&fit=crop',
  },
];

const DestinationsScreen = () => {
  const [destinations, setDestinations] = useState(MOCK_DESTINATIONS);

  const renderItem = ({ item }) => (
    <ListItem bottomDivider containerStyle={styles.listItem}>
      {/* 3. هذا هو المكون الجديد الذي يعرض الصورة */}
      <Avatar
        size="large"
        rounded
        source={{ uri: item.image }}
      />
      
      <ListItem.Content>
        <ListItem.Title style={styles.itemTitle}>{item.name}</ListItem.Title>
        <ListItem.Subtitle>{item.description}</ListItem.Subtitle>
      </ListItem.Content>
      <ListItem.Chevron />
    </ListItem>
  );

  return (
    <SafeAreaView style={styles.container}>
      <View style={styles.container}>
        <Text style={styles.title}>Explore Morocco</Text>
        <FlatList
          data={destinations}
          renderItem={renderItem}
          keyExtractor={item => item.id}
        />
      </View>
    </SafeAreaView>
  );
};

const styles = StyleSheet.create({
  container: {
    flex: 1,
    backgroundColor: '#fff',
  },
  title: {
    fontSize: 24,
    fontWeight: 'bold',
    paddingHorizontal: 16,
    paddingVertical: 10,
    marginTop: 10,
  },
  itemTitle: {
    fontWeight: 'bold',
  },
  listItem: {
    paddingVertical: 15,
  },
});

export default DestinationsScreen;

