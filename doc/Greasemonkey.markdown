##油猴子技巧 Greasemonkey_Hacks
#####Adding a Global Style[加入全局样式]
```
function addGlobalStyle(css) {
		try {
			var elmHead, elmStyle;
			elmHead = document.getElementsByTagName('head')[0];
			elmStyle = document.createElement('style');
			elmStyle.type = 'text/css';
			elmHead.appendChild(elmStyle);
			elmStyle.innerHTML = css;
		} catch (e) {
			if (!document.styleSheets.length) {
				document.createStyleSheet();
			}
			document.styleSheets[0].cssText += css;
		}
	}
```

#### Inserting or Removing a Single Style

```
//insert
document.styleSheets[0].insertRule('html,body{font-size:large}',0)

//remove
document.styleSheets[0].deleteRule(0);

```
#### modifying an Element's Style
>Tip : **float**在javascript表达式中表现为modify.style.cssFloat

```
	var modify = document.getElementById("foo");
	modify.style.backgroundColor ="red";
```