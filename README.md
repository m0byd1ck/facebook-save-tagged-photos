# Facebook save tagged photos
## About
Facebook save tagged photos is a script that can be run in FireFox scratchpad that will automatically save photos you are tagged in.

It is a JavaScript code that does nothing more than simulate the mouse clicks. You can set it running and leave it to complete. It takes appx. 10 seconds per photo (so may take a while if you have been busy).

It is not perfect and a bit hacky, but at the time of coding I could not find any other working tools. 

## Usage
* Open FireFox
* Login to facebook
* Browse to your profile then click photos
* Scroll down so all photos are loaded
* Open the scratchpad (Menu > Developer > Scratchpad)
* Paste in the JavaScript code from below
* Click run and watch as your posts are deleted

## Notes
### Will be deleted:
* If you get a dialog box to open a file, click "Do this automatically for files like this from now on"

## The Code
    
    var buttons = document.querySelectorAll('[data-tooltip="Edit or remove"]'), i;
    for (i = 0; i < buttons.length; ++i) {
        timeout = i*10000
        doSetTimeout(i, timeout);
    }
    
    function doSetTimeout(i, timeout) {
      setTimeout(function() { 
          buttons[i].scrollIntoView( true );
          window.scrollBy(0, -200);
          buttons[i].focus();
      }, timeout);
      setTimeout(function() { 
          buttons[i].click();
      }, (timeout+1000));
      setTimeout(function() { 
          var child = buttons[i].parentNode;
          var nodes = child.querySelectorAll('[data-label="Download"]');
          nodes[0].childNodes[0].click();
    
      }, (timeout+2000));
    }
    
# Testing
* I have tested the module on 19th September 2015 and it worked for me
* Use at your own risk, I do not offer any guarantee or warranty

# Licence
The code is released under [GNU GPL v3](http://www.gnu.org/licenses/gpl-3.0.en.html)