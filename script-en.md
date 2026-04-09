# Presentation Script — Web Fundamentals for CTF (English)

---

## Slide 1 — Title

Hey everyone — welcome. Today we're going to cover the fundamentals of how the web works. Not from a user perspective, but from a hacker's perspective. By the end of this, you'll understand exactly what's happening every time a browser loads a page — and more importantly, where things can go wrong.

---

## Slide 2 — Client and Server

So first question — when you type google.com into your browser, what actually happens? Most people think the website is "somewhere on the internet." But it's more specific than that. Every website lives on a server — a computer that's always on, always connected, always waiting. And your browser? That's the client. It connects to that server and says: "give me your homepage." The server finds it and sends it back.

---

## Slide 3 — What the Server Holds

Now, everything on a server that you can request is called a resource. Think of it like a file system. Every resource has a path — `/index.html`, `/login`, `/api/users`. This is important. In CTF challenges, a huge amount of finding flags comes down to knowing what paths exist on a server. Sometimes there are resources the developer forgot about — files that aren't linked anywhere, but they're still there if you know what to ask for. Like `/flag.txt`.

---

## Slide 4 — How They Talk

OK so the client wants to talk to the server. But here's a problem — your laptop might run Windows, the server is running Linux. They're completely different systems. How do they understand each other? They agree on a shared set of rules. That agreement is called a protocol. And the protocol of the web is HTTP — HyperText Transfer Protocol. It defines exactly how a request should look and exactly how a response should look. So it doesn't matter what OS or language either side uses — as long as both speak HTTP, they understand each other.

---

## Slide 5 — Request and Response

Every single thing that happens on the web is a request followed by a response. The request is what the client sends — it has a method, a path, headers, and sometimes a body. The response is what the server sends back — a status code, headers, and the actual content. Look at the image — this is what they actually look like. In CTF, everything you do — logging in, accessing pages, calling APIs — you're crafting requests and reading responses.

---

## Slide 6 — Request-Response Cycle

Let me show you this as an animation. Watch — the client sends a request. The server receives it, processes it, and sends a response back. Then the browser renders whatever came in the body. This is it. This is the entire web. Every website, every API, every login form — it all comes down to this one cycle, over and over.

---

## Slide 7 — Recap: Web Basics

Quick recap before we go deeper. Client and server — one asks, one answers. Resources — everything on the server has a path. HTTP — the protocol that makes communication possible. And every message has the same structure: a method, a path, a status code, a body. Keep these in your head. Everything we do from here is built on top of this.

---

## Slide 8 — HTTP Status Codes Overview

Now let's talk about status codes. Every response comes with a three-digit number that tells you what happened. They're grouped into ranges. 2xx means success. 3xx means redirect — go somewhere else. 4xx means the client made a mistake. 5xx means the server broke. You need to know these by heart. In CTF, the status code alone often tells you whether you're on the right track.

---

## Slide 9 — Common Status Codes

Here are the ones you'll actually see. 200 — worked fine. 201 — something was created. 301 and 302 — redirects, permanent and temporary. 403 — you're not allowed, but the resource exists. 404 — doesn't exist at all. 500 — server crashed. Pay special attention to 403. In CTF, a 403 means the thing is there — you just don't have permission yet. That's valuable information.

---

## Slide 10 — HTTP Methods Overview

Every request has a method — a verb that tells the server what you want to do. GET means retrieve something. POST means send something. PUT means replace something entirely. PATCH means update part of it. DELETE means remove it. OPTIONS asks what methods are even allowed. In web CTF, GET and POST are the ones you'll use most. But knowing the others matters — especially OPTIONS, which can sometimes reveal what a server is hiding.

---

## Slide 11 — GET

GET is the simplest method. It says: give me this resource. Every time you open a website, your browser is sending a GET request. The key thing about GET — the data is in the URL. Right there in the address bar, in your browser history, in the server logs. Which means: never put anything sensitive in a GET request. If you see a login system passing passwords in the URL, that's already a vulnerability.

---

## Slide 12 — POST

POST is for sending data. The difference from GET is where the data lives — in POST, it's in the request body, not the URL. So it's not visible in the address bar. But — and this is critical — that doesn't mean it's secure. Without HTTPS, anyone on the same network can still read the body. The body is not encrypted by default. HTTPS is what encrypts it. And in CTF, you're often looking at HTTP, not HTTPS.

---

## Slide 13 — GET vs POST

Side by side. GET — data in the URL, bookmarkable, cached by the browser, limited size. POST — data in the body, not in the URL, not cached, no size limit. The practical rule: GET is for fetching things, POST is for submitting things. Mixing them up — like a server that accepts sensitive data via GET — is a classic vulnerability you'll find in CTF challenges.

---

## Slide 14 — HTTP Request Anatomy

Now you know what methods and status codes are — let's see what an actual HTTP request looks like. The first line has three things: the method, the path, and the HTTP version. Then come the headers — key-value pairs that carry metadata. Host tells the server which domain you're talking to. User-Agent tells it what browser you're using. Accept tells it what format you want back. After all the headers, there's a blank line, and then the body if there is one.

---

## Slide 15 — HTTP Response Anatomy

And the response follows the same pattern. First line — HTTP version and the status code. Then headers. Content-Type tells you what's in the body. Set-Cookie is how the server assigns you a session — this is massive for CTF. Then the blank line, then the body — the actual HTML, JSON, whatever. Everything you see in your browser was inside a response body.

---

## Slide 16 — URL Anatomy

One more thing before the recap — the URL itself. It has parts. The protocol — HTTPS or HTTP — tells you how to connect. The domain — the address of the server. The path — which resource you want. Then the query parameters — extra data passed as key-value pairs in the URL, everything after the question mark. And the fragment — the part after the hash, which is handled by the browser, not the server. In CTF, query parameters are one of the first places you look for injection points.

---

## Slide 17 — HTTP Recap

That's HTTP. Status codes — 2xx good, 3xx redirect, 4xx your fault, 5xx their fault. Methods — GET reads, POST sends. Request and response both have a first line, headers, and a body. This is the language of the web. Everything in web security — SQL injection, XSS, authentication bypass, IDOR — happens inside HTTP messages. When you understand the message format, you understand where to attack.

---

## Slide 18 — HTML

So what does a server actually send back in the body? Usually HTML. HTML is the structure of a webpage. This is what it looks like with no styling — just raw HTML rendered by the browser with its default styles. Ugly, but it works. Every element you see on a page — a heading, a paragraph, a form, a button — is an HTML tag. And in CTF, you'll read HTML source constantly. Hidden fields, comments in the code, links that aren't visible — all of it is in the HTML.

---

## Slide 19 — CSS

Same page, but now with CSS. CSS is what controls how things look — colors, spacing, fonts, layout. Notice the difference: same structure, completely different appearance. For CTF purposes, CSS is less critical than HTML — but it's important to understand that it's a separate layer. Sometimes developers leave sensitive information in CSS files, or use CSS to hide elements they think users can't see.

---

## Slide 20 — JavaScript

And now JavaScript. This is what makes the page actually do something. Try it — type anything and click Log In. JavaScript is handling that click, reading your input, making a decision, and showing a response. Without JavaScript, that button does nothing at all. For CTF, JavaScript is gold. The source code runs in your browser — you can read it, modify it, and bypass client-side checks. If a website is doing validation in JavaScript, that validation can be disabled. If tokens or API endpoints are in the JavaScript, you can find them.

---

## Slide 21 — DevTools

Which brings us to your first real tool — browser DevTools. F12. Open it right now on any website and you can see everything. The Elements tab shows you the full HTML of the page, live. The Console lets you run JavaScript directly. The Network tab — this is the one you'll live in during CTF — shows every single HTTP request and response. You can see the method, the URL, the status code, the headers, the body. The Application tab shows cookies and local storage. This is all you need to start.

---

## Slide 22 — Final Recap

Let's close with the full picture. Client and server — request and response. Resources have paths. HTTP is the protocol. Status codes tell you what happened. Methods tell the server what to do. HTML is structure, CSS is style, JavaScript is behavior. And DevTools lets you see all of it. This is the foundation. Everything in web CTF — every injection, every bypass, every token leak — happens on top of what you just learned.

---

## Slide 23 — End

That's it for today. If you take one thing from this — open DevTools on the next website you visit. Look at the Network tab. You'll see everything we talked about in action. Read the requests, read the responses, try to understand what the site is doing. That habit alone will get you far. Good luck.
