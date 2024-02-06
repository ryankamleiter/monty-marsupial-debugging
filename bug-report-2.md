# Bug Report!

## Describe



**What is happening? What do you see?**

On page load the ready to transfer status was always rendering as "false."

**What _should_ be happening? What do you want to see?**

Koalas that are ready to transfer in the database should reflect that on the DOM.

## Isolate

**Is this problem client side? Server side? Elsewhere? How do you know?**

Client, server, and database were all affected by this bug. Browser console log gave an error of 500, there were errors on the server side console, and the DOM wasn't rendering properly. Also, the database wasn't interacting with the client through the server properly.

**What line of code is the error happening on?**

Paste the relevant code here:
```js
```
    UPDATE "koalas" 
        SET "readyToTransfer"= $2
        WHERE id=$1;

    const sqlParams = [koalaId, req.body.readyToTransfer];

    pool.query(sqlQuery, sqlParams)

Client.js:

          <div class="form-check form-switch">
            <input 
            class="form-check-input ready-to-transfer-toggle" 
            type="checkbox"
            ${koala.readyToTransfer ? 'checked' : ''}
            onclick="toggleReadyToTransfer(event)"
            />

And describe what it's doing wrong:

We were not properly sending the ready_to_transfer update to the database. 
readyToTransfer didn't exist but ready_to_transfer does.


**What tools did you use to isolate the error?**

- [X] `console.log()`
- [ ] Chrome debugger (_Sources_ panel)
- [ ] VSCode debugger
- [ ] Chrome Network Panel
- [ ] Postman
- [ ] Postico

<!-- Briefly describe how the tool helped you, and how you used it -->

console logging allowed us to see where the error was occuring (line and file)

## Fix

❗ Don't try to fix before first **describing** and **isolating!**

Briefly describe your fix:

Changed the casing of readyToTransfer to ready_to_transfer.
Changed the parameters of pool.query() from [koalaId, req.body.readyToTransfer] to sqlQuery, [koalaId]
Changed the sqlQuery to SET "ready_to_transfer"= NOT "ready_to_transfer"


**What tools did you use?**

- [ ] Fix one line of code. Then test using the debugger or `console.log()`s.
- [ ] Google search
- [X] Ask a pod mate for help
- [ ] Escalate

**Results**

<!-- Go back to your original description. Is the app behaving how you want it to, now? Describe the bug, technically: what was your code doing wrong, and how did you fix it. -->

The app can now update the ready to transfer status and render the database values to the DOM. The code wasn't interacting with the server, client, and database correctly. Because the update SQL query was not written correctly, this caused the client to output an internal server error.