---
title: How to Create a Navigation Menu
summary: Build a multi-tiered navigation UI.
---

# How to Create a Navigation Menu

In this how-to, we'll create a simple menu which you can use as the primary navigation for your website. This outputs a
top level menu with a nested second level using the `Menu` loop and a `Children` loop.

**app/templates/Page.ss**

```ss
<ul>
    <% loop $Menu(1) %>
        <li>
            <a href="$Link" title="Go to the $Title page" class="<% if $isCurrent %>current<% else_if $isSection %>section<% end_if %>">
                $MenuTitle
            </a>

            <% if $isSection %>
                <% if $Children %>
                    <ul class="secondary">
                        <% loop $Children %>
                            <li class="<% if $isCurrent %>current<% else_if $isSection %>section<% end_if %>"><a href="$Link">$MenuTitle</a></li>
                        <% end_loop %>
                    </ul>
                <% end_if %>
            <% end_if %>
        </li>
    <% end_loop %>
</ul>
```

## Related

* [Template Syntax](../syntax)
* [Common Variables](../common_variables)
