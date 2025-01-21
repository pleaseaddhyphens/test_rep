### Главная проблема
Из за нехватки опыта я начал костыли решения на хочу не задумываясь над тем как я буду поддерживать код.
Замечания на будущее при доработке софта.
1. Навешивать плагины, не затрагивая существующий код, т.к. его буду обновлять.
2. Новые фичи именно в виде плагинов а не хард код 

### Установка плагина на mac
 Если python стоит на конде, то легче установить через zip file устанавливать№

### Установка на ubuntu

Лучше прописать в pyproject, packages = [{include = "seltmodelplugin"}] и держать все в lowercase
### Gaphor startup


2.1. Install the latest [Python](https://www.python.org/downloads/windows/) environment 2.2. Check the python environment by typing: py -3.12 --version 3. Install GIt: winget install Git.Git 4.1. Install Graphviz from [official website](https://graphviz.org/download/). 4.2. Restart your PowerShell terminal as a normal user and check that the dot command is available: dot -?

5.1. If you need to use gaphor as a Python library only, just type pip install gaphor 5.2. Check if Gaphor is installed gaphor

If you would like to run Gaphor from command line, you should install the GTK-4 library. 6.1. Download latest GTK zip archive from [official repository](https://github.com/wingtk/gvsbuild/releases). 6.2. Unpack archive to C:\gtk\ 6.3. Add C:\gtk\bin to PATH as it showed in 1.4 and set it to the first row

+

*Все действия выполнять в PowerShell* 

>Дополнительно установил Gtk через MSYS2 MSys согластно [гайду](https://www.gtk.org/docs/installations/windows) 

Установил зависимости с 
poetry install. 
Для этого добавил папку `C:\Users\Valentin\pipx\venvs\poetry\Scripts` поместил в переменные среды (че это я не помню, сейчвс в переменных среды этого нет и все робит)
Далее согласно гайду
poetry run pre-commit install
poetry run pip install --force-reinstall (Resolve-Path C:\gtk\wheels\PyGObject*.whl)
poetry run pip install --force-reinstall (Resolve-Path C:\gtk\wheels\pycairo*.whl)
poetry run gaphor ^982ef1

 Для того чтобы запустить debugging in VS code нужно Set Up Poetry Environment in VS Code  by pressing `Ctrl+Shift+P` and typing "Python: Select Interpreter". Then, choose the interpreter from the Poetry environment (UPDATE: почему то не робит) 

**
### FileItem has no attribute filePath:
Нужно продублировать subject когда делаю ссылку на атрибут File:`self.subject.subject.filePath`. Так нужно потому что, self.subject ссылается на FileItem который в свою очередь имеет свой subject - File, у которого мы и читаем атрибут  

### toolbox item addition
1. Инициализировать tooldef в diagramtoolbox.py
2. при инициализации нужно сослаться на иконку (например, "gaphor-picture-symbolic") 
3. В new_item_factory передать item_class (как будет выглядеть) и subject_class (Логика). Разделение применрное, но за это отвечают разные файлы
5. Item_class определяется в diagramm/general/picture.py например. 
6. Subject_class определяется в core/modeling/coremodel.py (Дополнительно регистрируется в init) **НЕЛЬЗЯ напрямую этот файл править** Как генерировать код с помощью coder.py
	1. Попытался наследовать класс picture для записи пути до файла, возникла AssertionError. Нужно откатить изменения.
	2. Можно попробовать сослаться на другие классы.(ОТМЕНА, судя по всему нужно все таки другой subject class создавать, ругается, что на него уже ссылка есть)
7. В generalpropertypages.py инициализировать логику работы с иконкой.
8. В propertypges.ui настраивается вид gtk интерфейса правого окна, иконка переименовывается там.ч
### coder.py
Для генерации coremodel.py нужно декларировать override file, model file. Например
```python gaphor\codegen\coder.py models\Core.gaphor -r models\Core.override -o test_1.py```
''
Так же для генерации можно использовать poe: `poe coremodel`  Скрипт декларирован в pyproject.toml. для этого нужно естановить `pip install poethepoet`
### New profile model
Судя по всему в гофере нужно сначала определить модель элементов (находиться в папке Selt-dev/models) где импортировать название классов, далее через генератор кода сделать файл для subject classes 

### New plugin declaration
все по гайду, указать entry point at pyproject.toml. Потом повторить poetry run pre-commit install, poetry install

### 'Box' object has no attribute 'get_object' in gtk UI builder

`builder = self.construct()` возвращает объект gtkBox, у которого нет атрибута get_object.

### Обновление GUI при изменении модели
Нужно хранить builder object as a instance variable i.e.  Initialize it in `__init__` method as `self.builder = None` and then access that variable in the methods `self.builder = new_builder`
You can access that variable from other methods outside the construct()

### Не прикрепляется созданные file element к классам в гафоре
Попытался добавить File на диаграмму annotiaon (пере использовал элемент с presentation) линией комментария сейчас присасывается только к заметке но не к картинке или фотографии

The line divides the info that is  imported to [google docs](https://docs.google.com/document/d/1Zw0mVMEztTjDe2g9ITjtuQAhwSs3kTnyeBymqkWAo38/edit)

---
### Прикрепление comment line к новому елементу.
Нужно декларировать его в в файле diagram/general/connectors.py и исправить логику работы в классе `class CommentLineElementConnect(BaseConnector):`

### Обновление имени файла в дереве гафора
в treemodel.py в функции sync нужно добавить изменение No file на basename (element.filePath)

### Запуск Makefile windows
Установить ее на Винду можно с помощью ` winget install ezwinports.make`

Можно использовать Git bash чтобы запустить команду make из дериктории в которой он есть.

В самом makefile для запуска inkscape нужно прописать путь до inkscape.exe

### Установка нового профиля в gahor
Из промта:
>I declared the seltModel in the pyproject.toml `"SELT" = "gaphor.seltModel.modelinglanguage:seltModelLanguage"` . I chanhged the class name in the modelinglanguages.py from C4ModelLanguage onto "seltModelLanguage"

Потом нужно в новой папке скачать исходный код и переустановить зависимости с poetry как в [[Selt/Проблемы и решения gaphor#^982ef1]]


### Создание нового профиля
Нужно создать modelinglanguage.py, сгенерировать {modelname}.py. Определить propertypages.py and propertypages.ui
установить зависимости с иконками.
### Удаление плагина
Не решено (**Возможное решение это чистка дириктории и переустановка исходного кода**)
Не получается просто удалить плагин из гафора, на него ссылается bootstap, но в дериктории его уже и из pyproject.toml

```
File "C:\Users\Valentin\AppData\Local\Programs\Python\Python312\Lib\importlib\__init__.py", line 90, in import_module
    return _bootstrap._gcd_import(name[level:], package, level)
           ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "<frozen importlib._bootstrap>", line 1381, in _gcd_import
  File "<frozen importlib._bootstrap>", line 1354, in _find_and_load
  File "<frozen importlib._bootstrap>", line 1318, in _find_and_load_unlocked
ModuleNotFoundError: No module named 'gaphor.plugins.FileAttach'
``` 



### проблемы с прикреплением файла
**решено частично**, При попытке прикрепить файл он не может отобразиться на диаграмме, вылетает ошибка ниже 

Решается переустановкой гафора в локальной директории (скачать сурс, установить поетри и все зависимости) 

#### Ошибка
```
Traceback (most recent call last):
  File "C:\Users\Valentin\Desktop\SELT\SELT-dev\gaphor\diagram\painter.py", line 41, in paint_item
    item.draw(
  File "C:\Users\Valentin\Desktop\SELT\SELT-dev\gaphor\diagram\presentation.py", line 166, in draw
    self._shape.draw(
  File "C:\Users\Valentin\Desktop\SELT\SELT-dev\gaphor\diagram\shapes.py", line 273, in draw
    self.draw_vertical(context, bounding_box)
  File "C:\Users\Valentin\Desktop\SELT\SELT-dev\gaphor\diagram\shapes.py", line 330, in draw_vertical
    c.draw(child_context, Rectangle(x, y, w, h))
  File "C:\Users\Valentin\Desktop\SELT\SELT-dev\gaphor\diagram\shapes.py", line 573, in draw
    self.child.draw(new_context, bounding_box)
  File "C:\Users\Valentin\Desktop\SELT\SELT-dev\gaphor\diagram\shapes.py", line 528, in draw
    with cairo_state(context.cairo) as cr:
  File "C:\Users\Valentin\Desktop\SELT\SELT-dev\gaphor\diagram\shapes.py", line 38, in __exit__
    self._cr.restore()
gaphor.diagram.shapes.cairo.MemoryError: out of memory
```



### Сборка installer and portable версий

**Не решено**
Все согласно гайду. 
Нужно установить `winget install nsis 7zip`. Объявить путь в системных переменных до папок bin. Далее,
```
poetry install --only main,packaging,automation
poetry build
poetry run poe package
poetry run poe win-installer
```


Файлы собирает после сборки пакета есть ошибка. Ошибка при запуске `pyinstaller -y gaphor.spec`.
**Пробовал**: 
1. Собрать из чистой директории. Кстати после сборки пакета, запуск через poetry run работает плохо
2. Добавить в spec files путь до gtk
3. сменить флаг для сжатия upx = False
4. ```pacman -Suy pacman -S mingw-w64-x86_64-gtk4 mingw-w64-x86_64-python3 mingw-w64-x86_64-python3-gobject mingw-w64-x86_64-cairo mingw-w64-x86_64-gcc mingw-w64-x86_64-gobject-introspection```
#### Ошибка
```
Traceback (most recent call last):
  File "gaphor\__main__.py", line 6, in <module>
  File "gaphor\main.py", line 22, in main
  File "gaphor\entrypoint.py", line 13, in initialize
  File "gaphor\entrypoint.py", line 26, in load_entry_points
  File "importlib\metadata\__init__.py", line 205, in load
  File "importlib\__init__.py", line 90, in import_module
  File "<frozen importlib._bootstrap>", line 1381, in _gcd_import
  File "<frozen importlib._bootstrap>", line 1354, in _find_and_load
  File "<frozen importlib._bootstrap>", line 1304, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 488, in _call_with_frames_removed
  File "<frozen importlib._bootstrap>", line 1381, in _gcd_import
  File "<frozen importlib._bootstrap>", line 1354, in _find_and_load
  File "<frozen importlib._bootstrap>", line 1325, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 929, in _load_unlocked
  File "PyInstaller\loader\pyimod02_importers.py", line 378, in exec_module
  File "gaphor\plugins\diagramexport\__init__.py", line 14, in <module>
  File "<frozen importlib._bootstrap>", line 1354, in _find_and_load
  File "<frozen importlib._bootstrap>", line 1325, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 929, in _load_unlocked
  File "PyInstaller\loader\pyimod02_importers.py", line 378, in exec_module
  File "gaphor\ui\__init__.py", line 20, in <module>
  File "<frozen importlib._bootstrap>", line 1354, in _find_and_load
  File "<frozen importlib._bootstrap>", line 1325, in _find_and_load_unlocked
  File "<frozen importlib._bootstrap>", line 929, in _load_unlocked
  File "PyInstaller\loader\pyimod02_importers.py", line 378, in exec_module
  File "gaphor\ui\textfield.py", line 77, in <module>
  File "gi\module.py", line 130, in __getattr__
AttributeError: 'gi.repository.Gtk' object has no attribute 'Template'
```

### Как передать директорию где сохранена модель
Нужно обратиться к сервису `file_manager` который декларирован в .toml файле (по всей видимости он запускается и работает вместе с приложением). Используя сервис `ComponentRegestry` и метод get(). В классе generalpropertypage инициализирую на вход `ComponentRegestry`, судя по всему в этот момент происходит instantiation. Далее через мето get вызываю объект FileManager service, у которого обращаюсь к аттрибуту `_filepath`.  

Еще один вариант это записывать во временные файлы. тоесть просто в текстовый файл

### Как подписаться на событие в плагине

в методе `__init__` прописать `self.event_manager.subscribe(self._on_model_saved)` - подписаться на исполнение функции.
`_on_model_saved` декорировать с помощью `@event_handler`, например, так:
```
    @event_handler(ModelSaved)
    def _on_model_saved(self, event: ModelSaved) -> None:
        self.trigger_function(event.filename)
    def trigger_function(self, filename):
        print(f"Model has been saved to {filename}")
```


FAILED tests/test_architecture.py::test_diagram_package

## Убрал из тестов

[1443](https://github.com/pleaseaddhyphens/SELT-dev/actions/runs/11369894027/job/31628480553#step:8:1444)FAILED gaphor/diagram/general/tests/test_generalpropertypages.py::test_picture_property_select_valid_name - AssertionError: assert None == 'gaphor-24x24'

[1446](https://github.com/pleaseaddhyphens/SELT-dev/actions/runs/11369894027/job/31628480553#step:8:1447)FAILED gaphor/diagram/general/tests/test_generalpropertypages.py::test_picture_property_select_opens_dialog - AttributeError: 'NoneType' object has no attribute 'set_activate_signal_from_name'

gaphor/ui/tests/test_self_test

### Убрал из CI/CD подписание программы
```
name: 'Create macOS Application'
description: 'Create and Sign macOS Application Using PyInstaller'
inputs:
  version:
    description: 'Gaphor version number'
    required: true
  arch:
    description: 'macOS architecture'
    required: true
  base64_encoded_p12:
    description: 'base64_encoded_p12'
    required: true
  certpassword_p12:
    description: 'certpassword_p12'
    required: true
  notary_username:
    description: 'Username for notarizing'
    required: true
  notary_password:
    description: 'Password for notarizing'
    required: true
  notary_team_id:
    description: 'Team ID for notarizing'
    required: true
  sign_app:
    description: 'Build is performed on the main line'
    required: true
outputs:
  artifact:
    description: 'Build artifact'
    value: ${{ steps.dmg.outputs.artifact }}${{ steps.zip.outputs.artifact }}
runs:
  using: composite
  steps:
    - name: Ensure Homebrew Library Path
      run: test ! -d /opt/homebrew/lib || echo "DYLD_LIBRARY_PATH=/opt/homebrew/lib" >> $GITHUB_ENV
      shell: bash
    - name: Install Build Dependencies
      run: poetry install --only main,packaging --no-interaction
      shell: bash
    - name: Build Wheel
      run: poetry build
      shell: bash
    - name: Create Unsigned macOS Application
      if: inputs.sign_app != 'true'
      run: poetry run poe package
      shell: bash
    - name: Import codesign certificate
      if: inputs.sign_app == 'true'
      env:
        P12BASE64: ${{ inputs.base64_encoded_p12 }}
        P12PASSWORD: ${{ inputs.certpassword_p12 }}
      run: |
        P12FILE=$(mktemp)
        PASSWORD=$(openssl rand -base64 24)
        security create-keychain -p "$PASSWORD" temp.keychain
        echo "$P12BASE64" | base64 -D -o "$P12FILE"
        security import "$P12FILE" -k temp.keychain -f pkcs12 -T /usr/bin/codesign -T /usr/bin/security -P "$P12PASSWORD"
        rm -f "$P12FILE"
        security set-key-partition-list -S "apple-tool:,apple:" -k "$PASSWORD" temp.keychain
        security list-keychains -d user -s temp.keychain login.keychain
      shell: bash
    - name: Create Signed macOS Application
      if: inputs.sign_app == 'true'
      env:
        CODESIGN_IDENTITY: "Developer ID Application: Daniel Yeaw (Z7V37BLNR9)"
      run: poetry run poe package
      shell: bash
    - name: Store notary credentials
      if: inputs.sign_app == 'true'
      run: >
        xcrun notarytool store-credentials "notarytool-profile"
        --apple-id "${{ inputs.notary_username }}"
        --team-id "${{ inputs.notary_team_id }}"
        --password "${{ inputs.notary_password }}"
      shell: bash
    - name: Notarize app
      if: inputs.sign_app == 'true'
      env:
        PRODUCT_PATH: "_packaging/dist/Gaphor.app"
      run: |
        ditto -c -k --keepParent "${{ env.PRODUCT_PATH }}" "notarization.zip"
        xcrun notarytool submit "notarization.zip" --keychain-profile "notarytool-profile" --wait
      shell: bash
    - name: Staple app
      if: inputs.sign_app == 'true'
      env:
        PRODUCT_PATH: "_packaging/dist/Gaphor.app"
      run: xcrun stapler staple ${{ env.PRODUCT_PATH }}
      shell: bash
    - name: Create dmg
      id: dmg
      run: |
        cd _packaging
        # Improve hdiutil reliability
        # https://github.com/actions/runner-images/issues/7522#issuecomment-1556766641
        echo killing...; sudo pkill -9 XProtect >/dev/null || true;
        echo waiting...; while pgrep XProtect; do sleep 3; done;
        create-dmg --hdiutil-verbose --volname "Gaphor ${{ inputs.version }}-${{ inputs.arch }}" \
        --background "macos/background.png" \
        --window-pos 200 120 --window-size 700 400 --icon-size 100 \
        --icon "Gaphor.app" 200 240 --hide-extension "Gaphor.app" \
        --app-drop-link 500 240 "dist/Gaphor-${{ inputs.version }}-${{ inputs.arch }}.dmg" \
        "dist/Gaphor.app"
        echo "artifact=Gaphor-${{ inputs.version }}-${{ inputs.arch }}.dmg" >> $GITHUB_OUTPUT
      shell: bash
    - name: Notarize dmg
      if: inputs.sign_app == 'true'
      env:
        PRODUCT_PATH: "_packaging/dist/Gaphor-${{ inputs.version }}-${{ inputs.arch }}.dmg"
      run: |
        ditto -c -k --keepParent "${{ env.PRODUCT_PATH }}" "notarization.zip"
        xcrun notarytool submit "notarization.zip" --keychain-profile "notarytool-profile" --wait
      shell: bash
    - name: Staple .dmg
      if: inputs.sign_app == 'true'
      env:
        PRODUCT_PATH: "_packaging/dist/Gaphor-${{ inputs.version }}-${{ inputs.arch }}.dmg"
      run: xcrun stapler staple ${{ env.PRODUCT_PATH }}
      shell: bash
    - name: Delete temporary keychain
      if: inputs.sign_app == 'true'
      run: security delete-keychain temp.keychain
      shell: bash
    - name: Upload Gaphor-${{ inputs.version }}-${{ inputs.arch }}.dmg
      uses: actions/upload-artifact@65462800fd760344b1a7b4382951275a0abb4808 # v4.3.3
      with:
        name: Gaphor-${{ inputs.version }}-${{ inputs.arch }}.dmg
        path: _packaging/dist/Gaphor-${{ inputs.version }}-${{ inputs.arch }}.dmg
    - name: Upload Assets (release only)
      if: github.event_name == 'release'
      env:
        GH_TOKEN: ${{ github.token }}
      run: gh release upload ${{ inputs.version }} "_packaging/dist/Gaphor-${{ inputs.version }}-${{ inputs.arch }}.dmg"
      shell: bash
```


### Установка плагина
Устанавливаться должна в корень папки пользователя
`C:\Users\Valentin\.local\gaphor\plugins-2`
Плагин может использовать импорты из самого приложения, т.е. from gaphor import UML работает 
### Model saved on the disk (save )

закостылил
### Моргание при создании элемента на диаграмме (presetation)
Не решено

### Плохой перформанс при большом кол-ве элементов на экране.
Не решено

### Ошибка в консоли при добавлении файла как элемента 
##### ошибка
Traceback (most recent call last):
  File "C:\Users\Valentin\Desktop\SELT-dev-2\gaphor\ui\elementeditor.py", line 212, in create_pages
    page = adapter.construct()
           ^^^^^^^^^^^^^^^^^^^
  File "C:\Users\Valentin\Desktop\SELT-dev-2\gaphor\diagram\propertypages.py", line 288, in construct
    builder = new_builder("internals-editor")
              ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "C:\Users\Valentin\Desktop\SELT-dev-2\gaphor\diagram\propertypages.py", line 43, in new_builder
    translated_ui_string(package, f"{property_pages}.ui"), object_ids
    ^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
  File "C:\Users\Valentin\Desktop\SELT-dev-2\gaphor\i18n.py", line 77, in translated_ui_string
    ui_xml = etree.parse(ui_file)
             ^^^^^^^^^^^^^^^^^^^^
  File "C:\Users\Valentin\AppData\Local\pypoetry\Cache\virtualenvs\gaphor-Ubg7ze3c-py3.12\Lib\site-packages\defusedxml\common.py", line 100, in parse    
    return _parse(source, parser)
           ^^^^^^^^^^^^^^^^^^^^^^
  File "C:\Users\Valentin\AppData\Local\Programs\Python\Python312\Lib\xml\etree\ElementTree.py", line 1203, in parse
    tree.parse(source, parser)
  File "C:\Users\Valentin\AppData\Local\Programs\Python\Python312\Lib\xml\etree\ElementTree.py", line 571, in parse
    parser.feed(data)
  File "C:\Users\Valentin\AppData\Local\Programs\Python\Python312\Lib\xml\etree\ElementTree.py", line 1696, in feed
    self._raiseerror(v)
  File "C:\Users\Valentin\AppData\Local\Programs\Python\Python312\Lib\xml\etree\ElementTree.py", line 1603, in _raiseerror
    raise err
xml.etree.ElementTree.ParseError: junk after document element: line 320, column 0
