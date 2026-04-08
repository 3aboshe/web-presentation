# Nano Banana Prompts

Style for all images: soft flat illustration on a light background. Use blue (#2563eb) as accent. Objects should look like real things (laptops, servers, envelopes) but drawn in a clean flat vector style — no photorealism. Include text labels where they teach something. No characters with faces — faceless silhouettes are fine if needed. Keep it simple but not sterile.

---

## Prompt 1 — Client and Server (Slide 2)
**File:** `images/01-client-server.png`

> A flat illustration on a light background. On the left, an open laptop showing a browser with "google.com" in the address bar and the Google logo on the screen. On the right, a server rack with a few blinking lights and a small tag on it that says "google.com". Between them, a blue dashed arrow going right labeled "request" and a blue dashed arrow going left labeled "response". Below the laptop, a label says "Client". Below the server, a label says "Server". Clean flat vector style, soft shadows, light warm background.

---

## Prompt 2 — Resources on a server (Slide 3)
**File:** `images/02-resources.png`

> A flat illustration on a light background. A server rack on the left side with its door slightly open, revealing shelves inside. On each shelf, there are files and folders with labels sticking out like tabs: "/index.html", "/login", "/style.css", "/api/users", "/robots.txt", and one file glowing faintly in blue labeled "/flag.txt". A small arrow points to /flag.txt with an annotation bubble saying "hidden files are common in CTF". Clean flat vector style, soft colors, light background.

---

## Prompt 3 — HTTP Protocol (Slide 4)
**File:** `images/03-http-protocol.png`

> A flat illustration on a light background. A laptop on the left with a small Windows logo sticker on it. A server on the right with a small Linux penguin sticker on it. Between them, they are both holding the same open book labeled "HTTP" — like two people reading from the same rulebook. A small annotation above says "different systems, same rules". Clean flat vector style, no faces on any characters, soft colors, light background.

---

## Prompt 4 — Request and Response (Slide 5)
**File:** `images/04-request-response.png`

> A flat illustration on a light background. On the left, a hand holding a letter/envelope with writing visible on it: "GET /login", "Host: example.com", "Cookie: session=abc". The envelope is labeled "Request" at the top. On the right, another envelope coming back labeled "Response" with "200 OK", "Content-Type: text/html" written on it, and a small HTML page peeking out of the envelope. A blue dashed line connects the two envelopes showing the journey back and forth. Clean flat vector style, the hands are simple faceless silhouettes, soft colors, light background.

---

## Prompt 5 — DevTools Network tab (Slide 20)
**File:** `images/05-devtools.png`

> A flat illustration on a light background. A large browser window taking up most of the image. The browser has a tab labeled "CTF Challenge". On the right side of the browser, DevTools is open showing the Network tab. Inside the Network panel, a list of requests is visible as rows: "GET /index.html — 200", "GET /style.css — 200", "POST /login — 302", "GET /admin — 403" (this row highlighted in soft red). A faceless silhouette of a person sitting at the desk looking at the screen, with a small thought bubble showing a magnifying glass. Clean flat vector style, soft colors, light background.

---

## How to use

1. Generate each image in Nano Banana using the prompt above
2. Save to `images/` with the specified filename
3. Replace the `<div class="illustration">` placeholder in the matching slide:
   ```html
   <div class="illustration">
     <img src="images/01-client-server.png" alt="Client and server">
   </div>
   ```
