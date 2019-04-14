```css
.none_select{
    -webkit-user-select:none;
    -moz-user-select:none;
    -ms-user-select:none;
    -o-user-select:none;
    user-select:none;
}
```
onselectstart="return false" ： chrome 、ie 都支持，但firefox不支持！  
user-select：chrome firefox 都支持，ie不支持！  
上述操作对input标签失效，可用input标签的disabled="disabled" 来实现！  
ie7 还不支持onselectstart="return false"，（忽略！暂时没办法）