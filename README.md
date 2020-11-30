## Task
Detection of the chess board corners

## Solution
<li>Each corner is blurred with gaussian kernel.
<img src='logs\test_output\ground_true.png' width=256> </li>
<li>Training FPN segmentation Network using catalyst-dl.</li>
<li>Getting corner coordinates from mask via cv2.connectedComponentsWithStats.</li>

## eval
<img src='logs\test_output\0000.png' width=256> <img src='logs\test_output\0004.png' width=256>

## Идеи для улучшения:

<li>Ауги с поворотами:
    <li>Можно паддить до (256*256/2)**0.5*2 и вертеть на 360 градусов. </li>
    <li>Можно написать аккуратные повороты (строим вектор от центра поворота до искомого угла доски, и определяем для него максимальный угол поворота).</li>
    <li>Геометрические сжатия\растяжения.</li>
</li>
<li>Можно вообще попробовать искать прямые линии преобразованием Хафа (например) и искать их пересечения,
и обойтись классическим CV.</li>
<li>Можно натянуть маску на поверхность доски, так поучить и уже на предикт маске искать углы.</li>
<li>Для оценки разных моделей можно написать функцию L2 метрики между предикт точками и действительными (для этого придется отсортировать предикт точки, как было в Y_train)</li>

## Files
<li><b>Chess_Corners.ipynb</b> - Jupyter Notebook (preprocessing, training loop, evaluation and etc.)</li>
<li><b>\logs\segmentation\checkpoints\best.pth</b> - NN weights</li>
<li><b>Тестовое задание.pdf</b> - task description</li>