# Генератор обучающей выборки 
Изменение в работе с api сайта here.com:
Запрос `{{YOUR_APP_ID}}` и `{{YOUR_APP_CODE}}` сменился на запрос `{{YOUR_API_KEY}}`

Описание полученных результатов работы скрипта:

- плитки изображений имеют значения `row` и `column` (вероятно позиция плитки на карте, так же возможна выдача широты и долготы левого верхнего угла плитки)
- изображение и маска в формате `jpg`
- возможные разрешения изображения: `128*128` `256*256` `512*512`
- координаты забиваются вручную в config файл
- параметр `zoom` отвечает за приближение спутникового снимка (на мой взгляд оптимальные приближения начинаются с значения 15 и выше до 19, приближение 14 и ниже дает изображения и маски низкого качества)
- дата съемки: в документации на сайте существуют способы выкачивания спутниковых снимков с различными погодными условиями, величиной трафика и датой создания (в данном скрипте используется `newest/satellite.day`, то есть выкачиваются новейшие снятые изобряжения)

### Снимок и маска с метками building(белый), nature(черный):
<p>
<img src='dataset_building\15_11309_17235.jpg' width='250'>
<img src='dataset_building\15_11309_17235_m.jpg' width='250'>
</p>

### Снимок и маска с метками building(белый), railway(красный), highway(зеленый), water(синий), nature(черный): 
<p>
<img src='dataset\15_11323_17221.jpg' width='250'>
<img src='dataset\15_11323_17221_m.jpg' width='250'>
</p>

Замечания по качеству масок:
- плохое качество сегментации автомобильных дорог (появляются артефакты там, где они вообще не должны быть)
- сегментация зданий: кое-где существуют небольшие неточности в форме или площади зданий, но в целом маски не съезжают со своих снимков и практически точно отображают местоположение зданий на реальном снимке