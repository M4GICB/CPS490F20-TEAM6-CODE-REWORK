# CPS490F20-TEAM6-CODE-REWORK

# Claire:
* ### Changed comment above `socketio.on("userProfile", (userProfile) => {}`
  * Your comment: `// method for creating the individual user profiles`
  * Changed to: `// method for getting the profile info of an individual user`
  * Reason: Your comment did not make sense. Your function was not createing the profiles. That was something that Jake did. Your method is just getting the profile info from the database.

* ### Removal of following code block from `socketio.on("userProfile", (userProfile) => {}`
```
// if any of the inputs are null, reassign to 'blank'  
if(pUsername == null) {pUsername = "";}  
if(pDisplayName == null) {pDisplayName = "";}  
if(pTheme == null) {pTheme = "Default";}  
if(pVisibility == null) {pVisibility = "";}  
if(pLocation == null) {pLocation = "";}  
if(pAge == null) {pAge = "";}  
if(pLanguage == null) {pLanguage = "";}  
if(pSongs == null) {pSongs = "";}  
if(pMovies == null) {pMovies = "";}  
if(pInterests == null) {pInterests = "";}
```
  * This was done because of the changes made in Jake's section of profile creation.
* ### Completely Updated Comment Description of `socketio.on("userProfile", (userProfile) => {})`
* ### Condensed and moved following Code Block from `socketio.on("userProfile", (userProfile) => {})` into a function called `show_Profile_Info()`

```
// dynamically create the header based on individual user
document.getElementById("profileHeader").innerHTML = pUsername + "'s Profile";  
if(currentUser == pUsername){
    document.getElementById("colorThemes").style.display = "block";
    document.getElementById("profileInfo").style.display = "block";
    document.getElementById("privateProfile").style.display = "none";
    // document.getElementById("BUTTON FOR EDITING PROFILE ID").style.display = "block"; *****shows button - might need to be in a div???*****
    document.getElementById("edit_profile_button").style.display = "block";
    // profile to be shown for personal profiles                    
    document.getElementById("profileInfo").innerHTML =
        "<span class='profile_class'> Username: </span>" + pUsername + "<br><br>" +
        "<span class='profile_class'> Display name: </span>" + pDisplayName + "<br><br>" +
        "<span class='profile_class'> Color Theme: </span>" + pTheme + "<br><br>" +
        "<span class='profile_class'> Visibility: </span>" + pVisibility + "<br><br>" +
        "<span class='profile_class'> Location: </span>" + pLocation + "<br><br>" +
        "<span class='profile_class'> Age: </span>" + pAge + "<br><br>" +
        "<span class='profile_class'> Language: </span>" + pLanguage + "<br><br>" +
        "<span class='profile_class'> Songs: </span>" + pSongs + "<br><br>" +
        "<span class='profile_class'> Movies: </span>" + pMovies + "<br><br>" +
        "<span class='profile_class'> Interests: </span>" + pInterests + "<br><br>";
} else if(pVisibility == "public"){
    document.getElementById("profileInfo").style.display = "block";
    document.getElementById("privateProfile").style.display = "none";
    document.getElementById("colorThemes").style.display = "none";
    // document.getElementById("BUTTON FOR EDITING PROFILE ID").style.display = "none"; *****hides button*****
    document.getElementById("edit_profile_button").style.display = "none";

    // profile to be shown for others' profiles IF PUBLIC
    document.getElementById("profileInfo").innerHTML =
        "<span class='profile_class'> Username: </span>" + pUsername + "<br><br>" +
        "<span class='profile_class'> Display name: </span>" + pDisplayName + "<br><br>" +
        "<span class='profile_class'> Location: </span>" + pLocation + "<br><br>" +
        "<span class='profile_class'> Age: </span>" + pAge + "<br><br>" +
        "<span class='profile_class'> Language: </span>" + pLanguage + "<br><br>" +
        "<span class='profile_class'> Songs: </span>" + pSongs + "<br><br>" +
        "<span class='profile_class'> Movies: </span>" + pMovies + "<br><br>" +
        "<span class='profile_class'> Interests: </span>" + pInterests + "<br><br>";
} else if(pVisibility == "private"){
    // profile to be shown for others' profile IF PRIVATE
    document.getElementById("profileInfo").style.display = "none";
    document.getElementById("privateProfile").style.display = "block";
    document.getElementById("colorThemes").style.display = "none";
    // document.getElementById("BUTTON FOR EDITING PROFILE ID").style.display = "none"; *****hides button*****
    document.getElementById("edit_profile_button").style.display = "none";
}
```

  * This function takes in `currentUser`, `pUsername`, `pDisplayName`, `pTheme`, `pVisibility`, `pLocation`, `pAge`, `pLanguage`, `pSongs`, `pMovies`, and `pInterests`
    * These values are passed from the emmission you created earlier
  * This was done to be able to do `show profile` and `edit profile separately`
  
* ### Modified Logic for Displaying Profile Info
  * Condensed the following code block
```
// profile to be shown for others' profiles IF PUBLIC
                    document.getElementById("profileInfo").innerHTML = 
                        "<span class='profile_class'> Username: </span>" + pUsername + "<br><br>" + 
                        "<span class='profile_class'> Display name: </span>" + pDisplayName + "<br><br>" +
                        "<span class='profile_class'> Location: </span>" + pLocation + "<br><br>" +
                        "<span class='profile_class'> Age: </span>" + pAge + "<br><br>" +
                        "<span class='profile_class'> Language: </span>" + pLanguage + "<br><br>" +
                        "<span class='profile_class'> Songs: </span>" + pSongs + "<br><br>" +
                        "<span class='profile_class'> Movies: </span>" + pMovies + "<br><br>" +
                        "<span class='profile_class'> Interests: </span>" + pInterests + "<br><br>";
```
  * Instead of doing this logic twice (once to display the `if(currentUser == pUsername)` version and once to display `if(currentUser != pUsername)` version), we now show it once no matter who clicked it. And then, if `if(currentUser == pUsername)` we just display the visibility and theme at the bottom of the data.
   
* ### Theme values
  * Our current Theme Values are:
    * `Default`, `Theme1`, `Theme2`, and `Theme3`

* ### Removed color theme buttons
```
<!-- buttons to change color themes -->
<div id="colorThemes">
   <button type="button" id="colorTheme1" onclick="colorThemeChanger1()">Color Theme 1</button>
   <button type="button" id="colorTheme2" onclick="colorThemeChanger2()">Color Theme 2</button>
   <button type="button" id="colorTheme3" onclick="colorThemeChanger3()">Color Theme 3</button><br><br>
   <p id="colorThemeStatus"></p>
</div>
```

# Jake
* ### Changed profile Creation
  * changed profile creation to initialize blank values things to empty strings instead of `null`
  * changed profile creation to initialize theme values to empty `Defualt` instead of `defualt`
