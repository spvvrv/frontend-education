<h1>Позиционирование Position</h1>

**static:**
значение по умолчанию. Left, top, right, bottom не приведут ни к каким результатам. 
Можно применять к элементам float

**fixed:**
элемент будет зафиксирован относительно окна браузера и не будет менять положения при прокрутке. 
Отсчет начинается с левой верхней точки!
Нельзя применять к элементам float
Когда position задано как fixed, оно действует как абсолютное: вы можете установить координаты слева/справа и сверху/снизу.
Единственное отличие состоит в том, что точкой отсчёта является окно просмотра. Это означает, что фиксированный элемент не перемещается со страницей, он фиксируется на экране.

**relative:**
Пока мы не задали какие-либо позиции, то он будет находиться на своем месте. Как только добавим какие-либо параметры, то он будет смещаться относительно своего исходного положения! Оставшееся место заполняться не будет!
Нельзя применять к элементам float
При использовании относительного позиционирования, объект может свободно перемещаться, не нарушая макет.

**absolute:**
Элемент выпадает из потока: место, которое он занимал - заполнится другими данными. Элемент будет позиционироваться относительно родительского элемента, у которого любое другое позиционирование, кроме static!
Если у родительского элемента position static -> элемент позиционируется относительно <body> (чаще всего это окно браузера)
Если у родительского элемента position relative/absolute/fixed, то элемент позиционируется относительно родителя (так делаются модальные окна?). 
Нельзя применять к элементам float
Нужно задать координаты для каждой оси
Нужно указать ширину элемента, чтобы обеспечить размеры для контента - обеспечить предсказуемость его поведения

**z-index**
Перекрытие элементов друг-другом на z-оси (например при затемнении фона, например при вызове модального окна)ё

**sticky**
Крепится к определенному положению
Лучше делать через JavaScript

**float**
Определяет, по какой стороне будет выравниваться элемент, при этом остальные элементы будут обтекать его с других сторон (например текст обтекает картинки)
У плавающего элемента дб обязательно задана ширина, иначе элемент перестроится под размер контента в нем. 
Если плавающих элементов на странице много, то они будут выстраиваться друг за другом. Если ширины окна не хватит, то они будут переноситься на следующую строку. 
Плавающий элемент ведет себя как блочный!
Плавающий элемент выпадает из нормального блока!
"float first" - располагайте плавающий элемент в коде первым!

'''
float:
left
right
none
'''

float = block
К обтекаемым элементам автоматически применяется display: block и они в основном будут вести себя как блоки:
вы можете установить определённую высоту и ширину;
если высота не установлена, высотой элемента является line-height;
если применяется width: 100%, то будет выглядеть как блочный элемент.





Если родительский контейнер не оборачивает наши элементы, а "схлопнулся" внутри, то есть элементы выпали из нормального потока документа и родитель их не видит. Нужно использвать свойство clear
*clear*
Определяет, с какой стороны элемента нужно запретить его обтекание. 

position/assets/Снимок экрана 2022-07-03 в 17.53.33.png



ЕСЛИ НУЖНО СДЕЛАТЬ ГЛОБАЛЬНЫЙ ЛЭЙАУТ: ВЫСТРОИТЬ МЭИН, ФУТЕР И АСАЙД И ТД, ТО ИСПОЛЬЗУЙ GRID

ЕСЛИ НАДО СДЕЛАТЬ НАВИГАЦИЮ, ТО ИСПОЛЬЗУЙ FLEX


Чтобы перемещать элемент относительно родителя, у родителя должно быть задано положение: relative, absolute или fixed, а у дочернего элемента: absolute. В этом случае родитель станет точкой отсчета для передвижения дочернего элемента.
например 
section {
  position: relative; /* Превращает <section> в точку отсчёта для <p> */
}

p {
  position: absolute; /* Делает <p> свободно перемещаемым */
  bottom: 10px; /* 10px снизу */
  left: 20px; /* 20px слева */
}

Что произойдёт, если мы одновременно установим left и right?
Если ширина не задана, применение left: 0 и right: 0 растягивает элемент на всю ширину. Это эквивалент установки left: 0 и width: 100%.
Если ширина установлена, то значение right отбрасывается.


**Блочный элемент**
занимает всю доступную ширину и всегда начинается с новой строки.

* По ширине блочные элементы занимают всё допустимое пространство.


*Превращение ссылки в блок позволяет увеличить полезную площадь ссылки за счёт использования свойств width и height.*
В примере ссылкой является вся доступная по ширине область

a {
    display: block; /* Ссылка как блочный элемент */
}

**Строчный элемент**
Display: inline
* Размер элемента равен его содержимому плюс значения margin, border и padding.
* для строчных элементов margin работает только по горизонтали, но никак не вертикали

Подчеркнуть только заголовок:
  h1 {
    background: #EDE6CE; /* Цвет фона */
   }
   h1 span {
    margin: 16px; /* Отступы */
    padding: 1px; /* Поля */
    border-bottom: 2px solid #D71920; /* Линия снизу */
   }

    <body>
  <h1><span>Заголовок</span></h1>
 </body>

 Чтобы запретить перенос текста внутри элемента, добавьте свойство white-space со значением nowrap



 **Строчно-блочный элемент**
 display: inline-block

 * значение inline-block задано по умолчанию: <button>, <input>, <textarea>, <select>.
 * Высота и ширина элемента вычисляется браузером автоматически, исходя из содержимого блока.
* Размеры содержимого можно устанавливать через свойства width и height.
* Ширина блока получается сложением значений width, margin, border и padding.
* Высота блока получается сложением значений height, margin, border и padding.
* Несколько элементов идущих подряд располагаются на одной строке и переносятся на другую строку при необходимости.
* Элементы можно выравнивать по вертикали с помощью свойства vertical-align.
* Перенос текста считается за пробел.