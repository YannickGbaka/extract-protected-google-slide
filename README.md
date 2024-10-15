# Google Slide Content Extractor

**Disclaimer: This tool is for educational purposes only.**

This project demonstrates a method to extract content from Google Slides presentations. It is intended solely for educational and research purposes to understand web technologies and browser interactions. Users should be aware of and respect copyright laws and terms of service agreements.

## Important Notes

- Always obtain proper permissions before extracting or using content that doesn't belong to you.
- This tool should not be used to violate any terms of service or infringe on copyrights.
- The creators of this tool are not responsible for any misuse or legal consequences resulting from its use.

By using this tool, you acknowledge that you understand these terms and agree to use it responsibly and ethically.

### How to extract google slide content

copy and paste this code in the console


var atag = "punch-viewer-content",
btag = "-caption",
ctag = "aria-setsize",
dtag = "aria-posinset",
msvg = document.getElementsByTagName("svg"),
node = document.querySelectorAll('[class$="' + btag + '"]')[0],
view = document.getElementsByClassName(atag)[0],
size = node.getAttribute(ctag),
currentSlide = 0,  // Keep track of the current slide number
data = "",  // Initialize an empty string for data accumulation
func = () => {
    // Check the current slide position
    var i = node.getAttribute(dtag);

    // Ensure we're only adding new SVG content from the current slide
    if (i == currentSlide + 1) {
        // Add the current slide's SVG content to the accumulated data
        data += msvg[0].outerHTML;
        currentSlide++;  // Update the current slide count
    }

    // If we are on the last slide, display the collected content
    if (currentSlide == size) {
        escapeHTMLPolicy = trustedTypes.createPolicy("forceInner", {
            createHTML: (to_escape) => to_escape,
        });
        document.write(escapeHTMLPolicy.createHTML(data));
    } else {
        // Otherwise, move to the next slide and continue extracting content
        view.click();
        setTimeout(func, 500);  // Increase the delay to allow proper rendering
    }
};


// Start the extraction process
func();
