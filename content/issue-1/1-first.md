## HTML5 Draggable

| 事件类型 | 事件监听 | 触发时机 | 区域元素 |
| ------- | -- | -- | -- |
| **dragstart** | ondragstart  | 开始拖拽元素时触发 | 拖拽元素 |
| drag | ondrag  | 当元素拖拽期间按一定频率触发（在目标区域上） | 拖拽元素 |
| dragend | ondragend | 当拖拽的元素操作结束时触发（通过释放鼠标按钮或单击 escape 键）| 拖拽元素 |
| dragenter | ondragenter  | 拖拽元素进入目标区域时触发（一瞬间的触发） | 目标区域 |
| dragover | ondragover  | 拖拽元素在目标区域时触发（始终触发状态） | 目标区域 |
| dragleave | ondragleave  | 拖拽元素离开目标区域时触发（不松开鼠标的情况，可重复触发） | 目标区域 |
| drop | ondrop  | 拖拽元素在目标区域中松开鼠标时并放下被拖拽的元素触发 | 目标区域 |

#### Attention

> 鼠标松开的一瞬间，事件dragleave和事件drop不可共存，二者同时存在时，始终只能触发一个事件，而浏览器默认触发dragleave；若想触发drop 事件，则需要在dragover事件中阻止dragleave事件的默认行为。<br>
> **阻止方法**：event.preventDefault(); <br>
> **解释**：四个事件是一个连续触发的状态，上一个事件的结束往往是下一个事件的触发开始，所以在dragover中阻止事件的默认行为，即阻止的是dragleave的默认触发行为，从而实现drop事件的触发。


#### DataTransfer
##### 属性
| 属性 | 说明 |
| -- | -- |
| dropEffect | 获取或者设置当前选定的拖放操作类型。值为：none(禁止拖拽)、copy、link、move  |
| effectAllowed | 提供所有可用的操作类型。值是：none、copy、copyLink、copyMove、link、linkMove、move、all、uninitialized  |
| files | 包含数据传输中可用的所有本地文件的列表。如果拖动操作不涉及拖动文件，则此属性为空列表 |
| items (只读) | 提供一个包含所有拖动数据列表的 DataTransferItemList 对象 |
| types (只读) | 提供一个 dragstart 事件中设置的格式的 strings 数组 |

##### 方法
| 属性 | 说明 |
| -- | -- |
| setData(format, value) | 设置当前拖拽元素类型的数据。如果该类型的数据不存在，则将其添加到末尾，以便类型列表中的最后一项将是新的格式。如果该类型的数据已经存在，则在相同位置替换现有数据。  |
| getData(format) | 获取设置类型的数据，如果该类型的数据不存在或 data transfer 不包含数据，则返回空字符串  |
| clearData([format]) | 删除与给定类型关联的数据。类型参数是可选的。如果类型为空或未指定，则删除与所有类型关联的数据。如果指定类型的数据不存在，或者 data transfer 中不包含任何数据，则该方法不会产生任何效果  |
| setDragImage(img, xOffset, yOffset) | 发生拖动时，自定义图像， x 和 y 坐标是图像应该相对于鼠标指针出现的偏移量。  |

