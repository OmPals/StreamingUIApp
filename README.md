# StreamingUIApp

An interesting thing to know in this project is its MVVM!

## How to see this amazing UI right on your mobile phone:
(Make sure you have Visual Studio 2019 installed with Xamarin development package)
1) Download the repo, either zip or clone using git.
2) (unzip) Open the .sln file.
3) Trust this project (this project doesn't consume any internet so feel free!)
4) Connect your phone. On the menu bar, you will find your device name besides the "GREEN" PLAY BUTTON. Make sure it has USB debugging enabled.
5) On solution explorer on top right, right click on solution, then build the solution.
6) Right click on StreamingUIApp.Android in solution explorer and deploy it!
7) On your phone screen, there will probably a popup will show up asking your permission to get this app run on debugging mode, allow it!
DONE.

## What is MMVM!?
MVVM = Model View ViewModel
You'll probably see 3 folders inside StreamingUIApp, they are 1)Models 2)Views 3)ViewModels
1) Models: If you know databases, you might have already guessed what is models. Well, this is the same thing. You'll find the below code in it.
`public class Movie
    {
        public string MoviePicture { get; set; }
    }`
    Which you guessed right, we call a "Schema" in databases. class movie has a property MoviePicture, which is a string. Which we will know later that it refers to the filename of a particular movie's poster photo name!
2) Views: If you've been familiarized to Django, you've came across the terminology "Views" for the HTML files. 
Basically the views are files are XAML files in modern Xamarin development. People used to write C# code right away to define the view of the applocation, but now it has XAML support as well.
So, views define "How your app will look!". Multi page applications may have multiple XAML files. Anyways, wehn you click the arrow icon besides the XAML file, you'll also find a code-behind C# file, which is makes your app alive!
3) ViewModels: First time when we look at it, we might get confused that, why this even exists!? But later, this is the most important part!
public class MovieViewModel
    {
        public ObservableCollection<Movie> movie { get; set; }

        public MovieViewModel()
        {
            movie = new ObservableCollection<Movie>
            {
                new Movie { MoviePicture = "Movie0"},
                new Movie { MoviePicture = "Movie1"},
                new Movie { MoviePicture = "Movie2"},
                new Movie { MoviePicture = "Movie3"},
                new Movie { MoviePicture = "Movie4"},
                new Movie { MoviePicture = "Movie5"}  
            }; 
        }
    }
    
This is what we see in ViewModel. The entries here we see are the name of the movie poster image files. (.png files). We see ObservableCollection<Movie> file. Movie here refers to our model Movie which we defined in "Models" class.
This is some important stuff right here, becuase it contains the actual "data" which binds your application's view to the database of file addresses!

### Where these movie poster images come from?
If you look at your platform specific folder (Android OR IoS) in solution explorer, you'll find a "Resources" folder.
We need to store the image files "PLATFORM" specifically. Meaning, Android system picks image files from Resources>Drawable, where as IoS picks from Resources folder. Here we'll find every image that are used to build this amazing UI!
