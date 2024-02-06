# Bug Report!

## Describe

The column names in our SQL file were misaligned.  

**What is happening? What do you see?**

Name and color were out of order.

**What _should_ be happening? What do you want to see?**

They needed to be in the proper order.

## Isolate

**Is this problem client side? Server side? Elsewhere? How do you know?**

The problem was in the database SQL file.  It was impacting the server as well - as the server was not able to make sense of the data as it was. 

**What line of code is the error happening on?**

Paste the relevant code here:

   const sqlQuery = `
        INSERT INTO "koalas" 
            ("color", "name", "age", "ready_to_transfer", "notes") 
        VALUES 
            ($1, $2, $3, $4, $5)
    `;

And describe what it's doing wrong:

It was adding the values in the wrong sequence (under the wrong column headers).

**What tools did you use to isolate the error?**

- [ ] `console.log()`
- [ ] Chrome debugger (_Sources_ panel)
- [ ] VSCode debugger
- [ ] Chrome Network Panel
- [ ] Postman
- [X] Postico

<!-- Briefly describe how the tool helped you, and how you used it -->

Postico allowed to see how the table was being formatted, and how we needed to update it.

## Fix

❗ Don't try to fix before first **describing** and **isolating!**

Briefly describe your fix:

**What tools did you use?**

- [X] Fix one line of code. Then test using the debugger or `console.log()`s.
- [ ] Google search
- [X] Ask a pod mate for help (discussed as a pod)
- [ ] Escalate

**Results**

<!-- Go back to your original description. Is the app behaving how you want it to, now? Describe the bug, technically: what was your code doing wrong, and how did you fix it. -->

The app is now behaving as we want it to.  As the bug was the column header misalignment, when we updated those column headers, the code worked as expected.  Having the column headers reflected accurately on all the files allows the inputs to transfer to the database as they should.