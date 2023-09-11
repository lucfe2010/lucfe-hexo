### ejs

https://ejs.co

 EJS is a simple templating language that lets you generate HTML markup with plain JavaScript. No religiousness about how to organize things. No reinvention of iteration and control-flow. It's just plain JavaScript.

迭代
the process of repeating a mathematical or computing process or set of instructions again and again, each time applying it to the result of the previous stage
(computer science) executing the same set of instructions a given number of times or until a specified result is obtained

religiousness虔诚
the quality of being extremely conscientious

conscientious一丝不苟的,认真的
 Someone who is conscientious is very careful to do their work properly.


- Example

```jsx
<% if (user) { %>
  <h2><%= user.name %></h2>
<% } %>
```

- Tags

```ejs
<% 'Scriptlet' tag, for control-flow, no output
<%_ ‘Whitespace Slurping’ Scriptlet tag, strips all whitespace before it
<%= Outputs the value into the template (HTML escaped)
<%- Outputs the unescaped value into the template
<%# Comment tag, no execution, no output
<%% Outputs a literal '<%'
%> Plain ending tag
-%> Trim-mode ('newline slurp') tag, trims following newline
_%> ‘Whitespace Slurping’ ending tag, removes all whitespace after it
```


- Includes
Includes are relative to the template with the include call. (This requires the 'filename' option.) For example if you have "./views/users.ejs" and "./views/user/show.ejs" you would use <%- include('user/show'); %>.

You'll likely want to use the raw output tag (<%-) with your include to avoid double-escaping the HTML output.

```ejs
<ul>
  <% users.forEach(function(user){ %>
    <%- include('user/show', {user: user}); %>
  <% }); %>
</ul>
```


- Layouts
EJS does not specifically support blocks, but layouts can be implemented by including headers and footers, like so:

```ejs
<%- include('header'); -%>
<h1>
  Title
</h1>
<p>
  My page
</p>
<%- include('footer'); -%>
```
