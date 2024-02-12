# Import necessary libraries for Android application development
from kivy.app import App
from kivy.uix.boxlayout import BoxLayout
from kivy.uix.button import Button
from kivy.uix.label import Label
from kivy.uix.screenmanager import ScreenManager, Screen
from kivy.utils import platform
from kivy.core.window importWindow

# Create a class for the main screen
class MainScreen(Screen):
    def __init__(self, **kwargs):
        super(MainScreen, self).__init__(**kwargs)

        # Create the layout for the main screen
        layout = BoxLayout(orientation='vertical')

        # Create a label to display the playing time
        self.time_label = Label(text='0:00', size_hint=(1, 0.1))

        # Create buttons for stop, back, and next options
        stop_button = Button(text='Stop', size_hint=(1, 0.1))
        back_button = Button(text='Back', size_hint=(1, 0.1))
        next_button = Button(text='Next', size_hint=(1, 0.1))

        # Bind the button events to their respective functions
        stop_button.bind(on_release=self.stop_music)
        back_button.bind(on_release=self.back_music)
        next_button.bind(on_release=self.next_music)

        layout.add_widget(self.time_label)
        layout.add_widget(stop_button)
        layout.add_widget(back_button)
        layout.add_widget(next_button)

        self.add_widget(layout)

    # Function to stop the music
    def stop_music(self, instance):
        pass

    # Function to go back to the previous song
    def back_music(self, instance):
        pass

    # Function to go to the next song
    def next_music(self, instance):
        pass


# Create a class for the settings screen
class SettingsScreen(Screen):
    def __init__(self, **kwargs):
        super(SettingsScreen, self).__init__(**kwargs)

        # Create the layout for the settings screen
        layout = BoxLayout(orientation='vertical')

        # Create a button to go to the support page
        support_button = Button(text='Support', size_hint=(1, 0.1))

        # Bind the button event to the corresponding function
        support_button.bind(on_release=self.open_support_page)

        layout.add_widget(support_button)

        self.add_widget(layout)

    # Function to open the support page
    def open_support_page(self, instance):
        if platform == 'android':
            import android
            android.open_url('https://t.me/ZX_MUSIC_channel')


# Create a class for the third screen
class ThirdScreen(Screen):
    def __init__(self, **kwargs):
        super(ThirdScreen, self).__init__(**kwargs)

        # Create the layout for the third screen
        layout = BoxLayout(orientation='vertical')

        # Add widgets to the layout if needed

        self.add_widget(layout)


# Create a class for the screen manager
class MyScreenManager(ScreenManager):
    pass


# Create the main application class
class MusicApp(App):
    def build(self):
        # Set the window size
        Window.size = (400, 600)

        # Create an instance of the screen manager
        screen_manager = MyScreenManager()

        # Create the main screen and add it to the screen manager
        main_screen = MainScreen(name='main_screen')
        screen_manager.add_widget(main_screen)

        # Create the settings screen and add it to the screen manager
        settings_screen = SettingsScreen(name='settings_screen')
        screen_manager.add_widget(settings_screen)

        # Create the third screen and add it to the screen manager
        third_screen = ThirdScreen(name='third_screen')
        screen_manager.add_widget(third_screen)

        return screen_manager


# Run the application
if __name__ == '__main__':
    MusicApp().run()
        
