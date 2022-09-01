# useCalendar Hook 🚀 <img alt="useCalendar version" src="https://img.shields.io/npm/v/@atiladev/usecalendar.svg?style=flat-square&label=Version&labelColor=000000&color=3949AB">

[![made with expo](https://img.shields.io/badge/MADE%20WITH%20EXPO-000.svg?style=for-the-badge&logo=expo&labelColor=4630eb&logoWidth=20)](https://github.com/expo/expo)

> Updated to Expo SDK46

### This is an easy hook to use expo-calendar. It allows you:

- Get access permission to calendar
- Open settings to give access permission to calendar
- Create a new calendar and store it on your device
- Add events to the calendar
- Get all events
- Get calendarId
- Check if an event exists inside of the calendar created
- Delete the calendar and all events inside of it

### Install

```sh
$ npm install @atiladev/usecalendar
or
$ yarn add @atiladev/usecalendar
```

### You'll need install next libraries:

```sh
$ npx expo install expo-calendar expo-localization @react-native-async-storage/async-storage
```

### How to use it

Start by importing the `useCalendar` hook and then import the packages that you need to interact with the Calendar:

```js
import useCalendar from '@atiladev/usecalendar';

const {
  addEventsToCalendar,
  createCalendar,
  deleteCalendar,
  getCalendarId,
  getEvents,
  getPermission,
  isThereEvents,
  openSettings,
} = useCalendar('App_Name', '#BADA55', 'Calendar_Name');

const createCalAndEvent = async () => {
  const granted = await getPermission();

  if (granted) {
    await createCalendar();
    let eventExists = await isThereEvents();

    if (!eventExists) {
      try {
        addEventsToCalendar('Event title', new Date(), new Date());
      } catch (e) {
        // Something went wrong
      }
    }
  } else {
    openSettings();
  }
};

const removeCalendar = () => deleteCalendar();
```

#### useCalendar

```js
useCalendar(title: string, color: string, storeName: string);
```

useCalendar returns:

```js
getPermission: () => Promise<Calendar[] | undefined>

createCalendar: () => Promise<void>

addEventsToCalendar: (eventTitle: string, eventStartDate: Date, eventEndDate: Date) => Promise<void>

deleteCalendar: () => Promise<void>

openSettings: () => Promise<void>

isThereEvents: () => Promise<boolean>

getEvents: () => Promise<Calendar.Event[]>

getCalendarId: () => Promise<any>
```

If this hook is useful for you, please consider giving it a star. This does not mean very much but motivates us to continue working on this and adding new features. Thanks!

Developed with ❤️ by [Leandro Favre (AtilaDev)](https://github.com/AtilaDev-team)
