## CSS Selectors

In CSS, selectors are patterns used to select the element(s) you want to style.Use our [CSS Selector Tester](https://www.w3schools.com/csSref/trysel.php) to demonstrate the different selectors.

|   |   |   |
|---|---|---|
|Selector|Example|Example description|
|[.](https://www.w3schools.com/csSref/sel_class.php)[_class_](https://www.w3schools.com/csSref/sel_class.php)|.intro|Selects all elements with class="intro"|
|_.class1.class2_|.name1.name2|Selects all elements with both _name1_ and _name2_ set  <br>within its class attribute|
|_.class1 .class2_|.name1 .name2|Selects all elements with _name2_ that is a descendant of an  <br>element with  <br>_name1_|
|[#](https://www.w3schools.com/csSref/sel_id.php)[_id_](https://www.w3schools.com/csSref/sel_id.php)|\#firstname|Selects the element with id="firstname"|
|[*](https://www.w3schools.com/csSref/sel_all.php)|*|Selects all elements|
|[_element_](https://www.w3schools.com/csSref/sel_element.php)|p|Selects all <p> elements|
|[_element.class_](https://www.w3schools.com/csSref/sel_element_class.php)|p.intro|Selects all <p> elements with class="intro"|
|[_element,element_](https://www.w3schools.com/csSref/sel_element_comma.php)|div, p|Selects all <div> elements and all <p> elements|
|[_element_](https://www.w3schools.com/csSref/sel_element_element.php) [](https://www.w3schools.com/csSref/sel_element_element.php)[_element_](https://www.w3schools.com/csSref/sel_element_element.php)|div p|Selects all <p> elements inside <div> elements|
|[_element_](https://www.w3schools.com/csSref/sel_element_gt.php)[>](https://www.w3schools.com/csSref/sel_element_gt.php)[_element_](https://www.w3schools.com/csSref/sel_element_gt.php)|div > p|Selects all <p> elements where the parent is a <div> element|
|[_element_](https://www.w3schools.com/csSref/sel_element_pluss.php)[+](https://www.w3schools.com/csSref/sel_element_pluss.php)[_element_](https://www.w3schools.com/csSref/sel_element_pluss.php)|div + p|Selects the first <p> element that is placed immediately after <div> elements khass ykon mssdod w howa lwel|
|[_element1_](https://www.w3schools.com/csSref/sel_gen_sibling.php)[~](https://www.w3schools.com/csSref/sel_gen_sibling.php)[_element2_](https://www.w3schools.com/csSref/sel_gen_sibling.php)|p ~ ul|Selects every <ul> element that is preceded by a <p> element|
|[[](https://www.w3schools.com/csSref/sel_attribute.php)[_attribute_](https://www.w3schools.com/csSref/sel_attribute.php)[]](https://www.w3schools.com/csSref/sel_attribute.php)|[target]|Selects all elements with a target attribute|
|[[](https://www.w3schools.com/csSref/sel_attribute_value.php)[_attribute_](https://www.w3schools.com/csSref/sel_attribute_value.php)[=](https://www.w3schools.com/csSref/sel_attribute_value.php)[_value_](https://www.w3schools.com/csSref/sel_attribute_value.php)[]](https://www.w3schools.com/csSref/sel_attribute_value.php)|[target=_blank]|Selects all elements with target="_blank"|
|[[](https://www.w3schools.com/csSref/sel_attribute_value_contains.php)[_attribute_](https://www.w3schools.com/csSref/sel_attribute_value_contains.php)[~=](https://www.w3schools.com/csSref/sel_attribute_value_contains.php)[_value_](https://www.w3schools.com/csSref/sel_attribute_value_contains.php)[]](https://www.w3schools.com/csSref/sel_attribute_value_contains.php)|[title~=flower]|Selects all elements with a title attribute containing the word "flower"|
|[[](https://www.w3schools.com/csSref/sel_attribute_value_lang.php)[_attribute_](https://www.w3schools.com/csSref/sel_attribute_value_lang.php)[\|=](https://www.w3schools.com/csSref/sel_attribute_value_lang.php)[_value_](https://www.w3schools.com/csSref/sel_attribute_value_lang.php)[]](https://www.w3schools.com/csSref/sel_attribute_value_lang.php)|[lang\|=en]|Selects all elements with a lang attribute value equal to "en" or  <br>starting with "en-"|
|[[](https://www.w3schools.com/csSref/sel_attr_begin.php)[_attribute_](https://www.w3schools.com/csSref/sel_attr_begin.php)[^=](https://www.w3schools.com/csSref/sel_attr_begin.php)[_value_](https://www.w3schools.com/csSref/sel_attr_begin.php)[]](https://www.w3schools.com/csSref/sel_attr_begin.php)|a[href^="https"]|Selects every <a> element whose href attribute value begins with "https"|
|[[](https://www.w3schools.com/csSref/sel_attr_end.php)[_attribute_](https://www.w3schools.com/csSref/sel_attr_end.php)[$=](https://www.w3schools.com/csSref/sel_attr_end.php)[_value_](https://www.w3schools.com/csSref/sel_attr_end.php)[]](https://www.w3schools.com/csSref/sel_attr_end.php)|a[href$=".pdf"]|Selects every <a> element whose href attribute value ends with ".pdf"|
|[[](https://www.w3schools.com/csSref/sel_attr_contain.php)[_attribute_](https://www.w3schools.com/csSref/sel_attr_contain.php)[*=](https://www.w3schools.com/csSref/sel_attr_contain.php)[_value_](https://www.w3schools.com/csSref/sel_attr_contain.php)[]](https://www.w3schools.com/csSref/sel_attr_contain.php)|a[href*="w3schools"]|Selects every <a> element whose href attribute value contains the substring "w3schools"|
|[:active](https://www.w3schools.com/csSref/sel_active.php)|a:active|Selects the active link|
|[::after](https://www.w3schools.com/csSref/sel_after.php)|p::after|eInsert something after the content of each <p> element|
|[::before](https://www.w3schools.com/csSref/sel_before.php)|p::before|Insert something before the content of each <p> element|
|[:checked](https://www.w3schools.com/csSref/sel_checked.php)|input:checked|Selects every checked <input> element|
|[:default](https://www.w3schools.com/csSref/sel_default.php)|input:default|Selects the default <input> element|
|[:disabled](https://www.w3schools.com/csSref/sel_disabled.php)|input:disabled|Selects every disabled <input> element|
|[:empty](https://www.w3schools.com/csSref/sel_empty.php)|p:empty|Selects every <p> element that has no children (including text nodes)|
|[:enabled](https://www.w3schools.com/csSref/sel_enabled.php)|input:enabled|Selects every enabled <input> element|
|[:first-child](https://www.w3schools.com/csSref/sel_firstchild.php)|p:first-child|Selects every <p> element that is the first child of its parent|
|[::first-letter](https://www.w3schools.com/csSref/sel_firstletter.php)|p::first-letter|Selects the first letter of every <p> element|
|[::first-line](https://www.w3schools.com/csSref/sel_firstline.php)|p::first-line|Selects the first line of every <p> element|
|[:first-of-type](https://www.w3schools.com/csSref/sel_first-of-type.php)|p:first-of-type|Selects every <p> element that is the first <p> element of its parent|
|[:focus](https://www.w3schools.com/csSref/sel_focus.php)|input:focus|Selects the input element which has focus|
|[:fullscreen](https://www.w3schools.com/csSref/sel_fullscreen.php)|:fullscreen|Selects the element that is in full-screen mode|
|[:hover](https://www.w3schools.com/csSref/sel_hover.php)|a:hover|Selects links on mouse over|
|[:in-range](https://www.w3schools.com/csSref/sel_in-range.php)|input:in-range|Selects input elements with a value within a specified range|
|[:indeterminate](https://www.w3schools.com/csSref/sel_indeterminate.php)|input:indeterminate|Selects input elements that are in an indeterminate state|
|[:invalid](https://www.w3schools.com/csSref/sel_invalid.php)|input:invalid|Selects all input elements with an invalid value|
|[:lang(](https://www.w3schools.com/csSref/sel_lang.php)[_language_](https://www.w3schools.com/csSref/sel_lang.php)[)](https://www.w3schools.com/csSref/sel_lang.php)|p:lang(it)|Selects every <p> element with a lang attribute equal to "it" (Italian)|
|[:last-child](https://www.w3schools.com/csSref/sel_last-child.php)|p:last-child|Selects every <p> element that is the last child of its parent|
|[:last-of-type](https://www.w3schools.com/csSref/sel_last-of-type.php)|p:last-of-type|Selects every <p> element that is the last <p> element of its parent|
|[:link](https://www.w3schools.com/csSref/sel_link.php)|a:link|Selects all unvisited links|
|[::marker](https://www.w3schools.com/csSref/sel_marker.php)|::marker|Selects the markers of list items|
|[:not(](https://www.w3schools.com/csSref/sel_not.php)[_selector_](https://www.w3schools.com/csSref/sel_not.php)[)](https://www.w3schools.com/csSref/sel_not.php)|:not(p)|Selects every element that is not a <p> element|
|[:nth-child(](https://www.w3schools.com/csSref/sel_nth-child.php)[_n_](https://www.w3schools.com/csSref/sel_nth-child.php)[)](https://www.w3schools.com/csSref/sel_nth-child.php)|p:nth-child(2)|Selects every <p> element that is the second child of its parent|
|[:nth-last-child(](https://www.w3schools.com/csSref/sel_nth-last-child.php)[_n_](https://www.w3schools.com/csSref/sel_nth-last-child.php)[)](https://www.w3schools.com/csSref/sel_nth-last-child.php)|p:nth-last-child(2)|Selects every <p> element that is the second child of its parent, counting from the last child|
|[:nth-last-of-type(](https://www.w3schools.com/csSref/sel_nth-last-of-type.php)[_n_](https://www.w3schools.com/csSref/sel_nth-last-of-type.php)[)](https://www.w3schools.com/csSref/sel_nth-last-of-type.php)|p:nth-last-of-type(2)|Selects every <p> element that is the second <p> element of its parent, counting from the last child|
|[:nth-of-type(](https://www.w3schools.com/csSref/sel_nth-of-type.php)[_n_](https://www.w3schools.com/csSref/sel_nth-of-type.php)[)](https://www.w3schools.com/csSref/sel_nth-of-type.php)|p:nth-of-type(2)|Selects every <p> element that is the second <p> element of its parent|
|[:only-of-type](https://www.w3schools.com/csSref/sel_only-of-type.php)|p:only-of-type|Selects every <p> element that is the only <p> element of its parent|
|[:only-child](https://www.w3schools.com/csSref/sel_only-child.php)|p:only-child|Selects every <p> element that is the only child of its parent|
|[:optional](https://www.w3schools.com/csSref/sel_optional.php)|input:optional|Selects input elements with no "required" attribute|
|[:out-of-range](https://www.w3schools.com/csSref/sel_out-of-range.php)|input:out-of-range|Selects input elements with a value outside a specified range|
|[::placeholder](https://www.w3schools.com/csSref/sel_placeholder.php)|input::placeholder|Selects input elements with the "placeholder" attribute specified|
|[:read-only](https://www.w3schools.com/csSref/sel_read-only.php)|input:read-only|Selects input elements with the "readonly" attribute specified|
|[:read-write](https://www.w3schools.com/csSref/sel_read-write.php)|input:read-write|Selects input elements with the "readonly" attribute NOT specified|
|[:required](https://www.w3schools.com/csSref/sel_required.php)|input:required|Selects input elements with the "required" attribute specified|
|[:root](https://www.w3schools.com/csSref/sel_root.php)|:root|Selects the document's root element|
|[::selection](https://www.w3schools.com/csSref/sel_selection.php)|::selection|Selects the portion of an element that is selected by a user|
|[:target](https://www.w3schools.com/csSref/sel_target.php)|\#news:target|Selects the current active #news element (clicked on a URL containing that anchor name)|
|[:valid](https://www.w3schools.com/csSref/sel_valid.php)|input:valid|Selects all input elements with a valid value|
|[:visited](https://www.w3schools.com/csSref/sel_visited.php)|a:visited|Selects all visited links|

p:nth-child(3n){

/*select every thid element*/

![[image-1668896097474.jpg7267573525132842655.jpg]]

}

p: nth-child(-n+3) {

/*from the third element to the previous elements*/

}

![[image-1668896197799.jpg4553522521800594091.jpg]]

p:nth-child(n+3){

/*from the 3 child to bottoms items lte7t*/

}

![[image-1668896262860.jpg171511942515559314.jpg]]