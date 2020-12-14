<!doctype html>

<html>
<head>
    <meta charset="utf-8">
    <title>Дерево</title>
    <style>
        .checked{
            background-color: blue;
        }
        .unchecked{
            background-color: white;
        }
    </style>
</head>
<body>
    <h1>Дерево</h1> 
    <input type="button" value="Создать" onclick="newChild()">
    <input type="button" value="Переименовать" onclick="changeName()">
    <input type="button" value="Удалить" onclick="remove()"><br>
    <div id="0">Корневой элемент</div>
    <script>
        var id = 0;
        var oldest = document.getElementById('0');
        var focus = false;
        oldest.classList.add('unchecked');
        oldest.addEventListener('click', highlite);
        oldest.style.marginLeft = '10px';
        function highlite(event){
            if (focus){focus.classList.remove('checked');focus.classList.toggle('unchecked');}
            focus = event.target;
            focus.classList.toggle('checked');
            focus.classList.toggle('unchecked');
        }
        function newChild(){
            focus.style.position = 'relative';
            element = document.createElement('div');
            element.id = id + 1;
            element.textContent = prompt();
            element.style.position = 'relative';
            element.style.left = '17px';
            element.style.width = '100%';
            element.classList.add('unchecked');
            element.addEventListener('click', highlite);
            focus.appendChild(element);
            if (focus.children.length == 1){
                var btn = document.createElement('img');
                btn.id = String(focus.id) + 'png';
                btn.src = 'minus.png'
                btn.style.position = 'absolute';
                btn.style.left = '-10px';
                btn.style.top = '0';
                btn.classList.add('minus');
                btn.addEventListener('click', folder);
                focus.appendChild(btn);
            }
            ++id;
        }
        function changeName(){
            focus.style.textContent = prompt();
        }
        function remove(){
            focus.remove();
        }
        function folder(event){
            var elem = event.target;
            var id = parseInt(elem.id);
            var child = document.getElementById(id);
            var children = child.children;
            if (elem.classList.contains('minus')){    
                for (var i = 0; i < children.length; ++i){
                    if (!children[i].id.includes('png')){
                        children[i].style.visibility = 'hidden';
                    }
                    children[i].style.position = 'absolute';
                    if (children[i].children.length > 0){fold(children[i].children)}
                }
                elem.classList.remove('minus');
                elem.classList.add('plus');
                elem.src = 'plus.png';
            }
            else{
                elem.src = 'minus.png';
                elem.classList.remove('plus');
                elem.classList.add('minus');
                for (var i = 0; i < children.length; ++i){
                    children[i].style.visibility = 'visible';
                    if (!children[i].id.includes('png')){
                        children[i].style.position = 'relative';
                    }
                    if (children[i].children.length > 0){unfold(children[i].children)}
                }
            }
        }
        function fold(elems){
            for (var i = 0; i < elems.length; ++i){
                elems[i].style.visibility = 'hidden';
                elems[i].style.position = 'absolute';
                if (elems[i].children.length > 0){fold(elems[i].children)}
            }
        }
        function unfold(elems){
            for (var i = 0; i < elems.length; ++i){
                elems[i].style.visibility = 'visible';
                if (!elems[i].id.includes('png')){
                    elems[i].style.position = 'relative';
                }
                else{
                    elems[i].src = 'minus.png';
                    elems[i].classList.remove('plus');
                    elems[i].classList.add('minus');
                }
                if (elems[i].children.length > 0){unfold(elems[i].children)}
            }
        }
    </script>
</body>
</html>
