## My Custom Bambdas

Bambdas for various tasks. The JSON files are for loading directly into Burp Bambda editor. No copy/paste required. 

`annotateXCorrelationHeaders.bambda`: Highlight Burp history entries which contain log correlation headers in either the request or response. Blue if they're found in the request, orange in the response, or magenta for both. Will add a note to the request showing which headers were detected. This can also be easily updated for any header of your choosing on the fly in the Burp Bambda editor if need be.

`reflectedGadgetHunter.bambda`: Highlights and annotates any requests which contain a specified canary in the response. Responses containing the canary in headers will be pink, and responses containing the reflected canary in response body will be green. Instances where the canary is actually reflected in the Location header are highlighted in red.

#### Usage Examples
- Add a match/replace rule in Burp to add an X-Forwarded-Host header to every request with a canary as the value. Any highlighted requests could then be probed for web cache poisoning issues.
- Could be applied to the Logger tab so after extensive fuzzing with Intruder you could highlight any requests with canary in the response body could be investigated for XSS potential.

#### Potential To-Dos
- Update the `reflectedGadgetHunter.bambda` to only highlight on certain response content types.
- Separate the Location header canary detection functionality into it's own bambda, and dynamically grab the value of any headers like X-Forwarded-Host, X-Forwarded-For, etc, and highlight when they are reflected in Location.
