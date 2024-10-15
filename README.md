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
