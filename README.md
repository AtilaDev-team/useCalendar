# useCalendar Hook 🚀 <img alt="useCalendar version" src="https://img.shields.io/npm/v/@atiladev/usecalendar.svg?style=flat-square&label=Version&labelColor=000000&color=3949AB">

[![made with expo](https://img.shields.io/badge/MADE%20WITH%20EXPO-000.svg?style=for-the-badge&logo=expo&labelColor=4630eb&logoWidth=20)](https://github.com/expo/expo)

## Updated to Expo SDK45

### This is an easy hook to use expo-calendar. It allows you:

- Get access permission to calendar
- Open settings to give access permission to calendar
- Create a new calendar and store it on your device
- Add events to this calendar
- Check if exist some event inside of this calendar created
- Delete the calendar and all events inside of it

### How to use it

```js
import useCalendar from '@atiladev/usecalendar';

const {
  getPermission,
  createCalendar,
  addEventsToCalendar,
  deleteCalendar,
  openSettings,
  isThereEvents,
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

const RemoveCalendar = () => deleteCalendar();
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
```

Developed with ❤️ by [Leandro Favre AtilaDev](https://github.com/AtilaDev-team)
