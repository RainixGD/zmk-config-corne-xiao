# ZMK config: Corne XIAO

Прошивка [ZMK](https://zmk.dev) для сплит-клавиатуры **Corne XIAO rev2** в варианте с **6 колонками** на контроллерах Seeed XIAO nRF52840 (`xiao_ble`).

## Возможности

- Беспроводной сплит: левая половина — central (подключается к компьютеру), правая — peripheral
- Энкодеры EC11 на обеих половинах: слева — громкость, справа — PgUp/PgDn
- Поддержка [ZMK Studio](https://zmk.dev/docs/features/studio) (разблокировка — одновременное нажатие двух левых верхних клавиш)
- Индикация статуса встроенным RGB-светодиодом XIAO через [zmk-rgbled-widget](https://github.com/caksoylar/zmk-rgbled-widget)
- Глубокий сон для экономии батареи

## Структура

| Путь | Назначение |
|---|---|
| `build.yaml` | Какие прошивки собирать |
| `config/west.yml` | Зависимости: ZMK и zmk-rgbled-widget |
| `config/corne_xiao.conf` | Пользовательские Kconfig-опции |
| `boards/shields/corne_xiao/` | Описание железа: матрица, пины, энкодеры, раскладка по умолчанию (`corne_xiao.keymap`) |
| `dts/layouts/corne_xiao/6column.dtsi` | Физическая раскладка для ZMK Studio |

## Сборка

Прошивка собирается в GitHub Actions при каждом push. Готовые файлы находятся в артефактах запуска workflow во вкладке **Actions**:

- `corne_xiao_left` — левая половина
- `corne_xiao_right` — правая половина

## Прошивка

1. Подключите половину по USB и дважды быстро нажмите кнопку reset на XIAO — появится USB-накопитель.
2. Скопируйте на него соответствующий `.uf2` файл.
3. Повторите для второй половины.
