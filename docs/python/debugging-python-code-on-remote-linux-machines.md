---
title: Kod Debugowania języka Python na zdalnych komputerach z systemem Linux
description: Program Visual Studio służy do debugowania kodu języka Python uruchomionego na zdalnych komputerach z systemem Linux, w tym niezbędnych kroków konfiguracji, zabezpieczeń i rozwiązywania problemów.
ms.date: 12/06/2018
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: e718a5610d9539e3e2a89af0a9de502ebfd168a7
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "62962552"
---
# <a name="remotely-debug-python-code-on-linux"></a>Zdalne debugowanie kodu Języka Python w systemie Linux

Program Visual Studio może uruchamiać i debugować aplikacje Języka Python lokalnie i zdalnie na komputerze z systemem Windows (zobacz [Zdalne debugowanie](../debugger/remote-debugging.md)). Może również debugować zdalnie na innym systemie operacyjnym, urządzeniu lub implementacji Języka Python innych niż CPython przy użyciu [biblioteki ptvsd](https://pypi.python.org/pypi/ptvsd).

Podczas korzystania z ptvsd, kod Języka Python jest debugowany hostuje serwer debugowania, do którego visual studio można dołączyć. Ten hosting wymaga niewielkiej modyfikacji kodu w celu zaimportowania i włączenia serwera, a także może wymagać konfiguracji sieci lub zapory na komputerze zdalnym, aby zezwolić na połączenia TCP.

|   |   |
|---|---|
| ![ikona kamery filmowa dla wideo](../install/media/video-icon.png "Obejrzyj film") | Aby zapoznać się z wprowadzeniem do zdalnego debugowania, zobacz [Deep Dive: Debugowanie zdalne między platformami](https://youtu.be/y1Qq7BrV6Cc) (youtube.com, 6m22s), które ma zastosowanie zarówno do programu Visual Studio 2015, jak i 2017. |

## <a name="set-up-a-linux-computer"></a>Konfigurowanie komputera z systemem Linux

Do wykonania tego przewodnika potrzebne są następujące elementy:

- Komputer zdalny z systemem Python w systemie operacyjnym, takim jak Mac OSX lub Linux.
- Port 5678 (przychodzący) otwarty na zaporze tego komputera, co jest ustawieniem domyślnym dla zdalnego debugowania.

Maszynę [wirtualną systemu Linux](/azure/virtual-machines/linux/creation-choices) można łatwo utworzyć na platformie Azure i uzyskać do niej dostęp za pomocą [pulpitu zdalnego](/azure/virtual-machines/linux/use-remote-desktop) z systemu Windows. Ubuntu dla maszyny Wirtualnej jest wygodne, ponieważ Python jest zainstalowany domyślnie; w przeciwnym razie zobacz listę na [Zainstaluj wybraną interpreter języka Python, aby](installing-python-interpreters.md) uzyskać dodatkowe lokalizacje pobierania języka Python.

Aby uzyskać szczegółowe informacje na temat tworzenia reguły zapory dla maszyny Wirtualnej platformy Azure, zobacz [Otwieranie portów na maszynie Wirtualnej na platformie Azure przy użyciu witryny Azure portal.](/azure/virtual-machines/windows/nsg-quickstart-portal)

## <a name="prepare-the-script-for-debugging"></a>Przygotowanie skryptu do debugowania

1. Na komputerze zdalnym utwórz plik języka Python o nazwie *guessing-game.py* z następującym kodem:

    ```python
    import random

    guesses_made = 0
    name = input('Hello! What is your name?\n')
    number = random.randint(1, 20)
    print('Well, {0}, I am thinking of a number between 1 and 20.'.format(name))

    while guesses_made < 6:
        guess = int(input('Take a guess: '))
        guesses_made += 1
        if guess < number:
            print('Your guess is too low.')
        if guess > number:
            print('Your guess is too high.')
        if guess == number:
            break
    if guess == number:
        print('Good job, {0}! You guessed my number in {1} guesses!'.format(name, guesses_made))
    else:
        print('Nope. The number I was thinking of was {0}'.format(number))
    ```

1. Zainstaluj `ptvsd` pakiet w swoim `pip3 install ptvsd`środowisku za pomocą programu .
   >[!NOTE]
   >Dobrym pomysłem jest nagranie wersji ptvsd, która jest zainstalowana w przypadku, gdy jest potrzebna do rozwiązywania problemów; [na liście ptvsd znajdują](https://pypi.python.org/pypi/ptvsd) się również dostępne wersje.

1. Włącz zdalne debugowanie, dodając poniższy kod *w*najwcześniejszym możliwym punkcie guessing-game.py przed innym kodem. (Chociaż nie jest to ścisłe wymaganie, nie można debugować żadnych wątków tła zrodził się przed wywołaniem `enable_attach` funkcji.)

   ```python
   import ptvsd
   ptvsd.enable_attach()
   ```

1. Zapisz plik i `python3 guessing-game.py`uruchom plik . Wywołanie `enable_attach` działa w tle i czeka na połączenia przychodzące, jak w przeciwnym razie interakcji z programem. W razie `wait_for_attach` potrzeby funkcję można `enable_attach` wywołać po zablokowaniu programu, dopóki debuger nie zostanie dołączony.

> [!Tip]
> Oprócz `enable_attach` i `wait_for_attach`, ptvsd zapewnia również `break_into_debugger`funkcję pomocnika , który służy jako programowy punkt przerwania, jeśli debuger jest dołączony. Istnieje również `is_attached` funkcja, `True` która zwraca, jeśli debuger jest dołączony (należy pamiętać, że `ptvsd` nie ma potrzeby, aby sprawdzić ten wynik przed wywołaniem innych funkcji).

## <a name="attach-remotely-from-python-tools"></a>Dołączanie zdalnie z narzędzi Python

W tych krokach ustawiamy prosty punkt przerwania, aby zatrzymać proces zdalny.

1. Utwórz kopię pliku zdalnego na komputerze lokalnym i otwórz go w programie Visual Studio. Nie ma znaczenia, gdzie znajduje się plik, ale jego nazwa powinna być zgodna z nazwą skryptu na komputerze zdalnym.

1. (Opcjonalnie) Aby mieć IntelliSense dla ptvsd na komputerze lokalnym, zainstaluj pakiet ptvsd w środowisku Pythona.

1. Wybierz **debugowanie** > **Dołącz do procesu**.

1. W wyświetlonym oknie dialogowym **Dołącz do procesu** ustaw typ **połączenia** na **zdalny język Python (ptvsd).** (W starszych wersjach programu Visual Studio te polecenia mają nazwy **Transport** i **Python zdalnego debugowania**.)

1. W polu **Obiekt docelowy połączenia** **(Kwalifikator** w starszych wersjach) wprowadź miejsce, `tcp://<ip_address>:5678` w `<ip_address>` którym znajduje `:5678` się komputer zdalny (który może być adresem jawnym lub nazwą, taką jak myvm.cloudapp.net) i jest zdalnym numerem portu debugowania.

1. Naciśnij **klawisz Enter,** aby wypełnić listę dostępnych procesów ptvsd na tym komputerze:

    ![Wprowadzanie obiektu docelowego połączenia i wyświetlanie procesów](media/remote-debugging-qualifier.png)

    Jeśli po zapełnieniu tej listy uruchomisz inny program na komputerze zdalnym, wybierz przycisk **Odśwież.**

1. Wybierz proces do debugowania, a następnie **Dołącz**lub kliknij dwukrotnie proces.

1. Visual Studio następnie przełącza się w tryb debugowania, podczas gdy skrypt nadal działa na komputerze zdalnym, zapewniając wszystkie możliwości [debugowania](debugging-python-in-visual-studio.md) zwykle. Na przykład ustaw punkt przerwania w wierszu, `if guess < number:` a następnie przełącz się na komputer zdalny i wprowadź inne przypuszczenie. Po zrobienie tego program Visual Studio na komputerze lokalnym zatrzymuje się w tym punkcie przerwania, pokazuje zmienne lokalne i tak dalej:

    ![Visual Studio wstrzymuje debugowanie po osiągnięciu punktu przerwania](media/remote-debugging-breakpoint-hit.png)

1. Po zatrzymaniu debugowania program Visual Studio odłącza się od programu, który nadal działa na komputerze zdalnym. ptvsd kontynuuje również nasłuchiwanie do dołączania debugerów, dzięki czemu można ponownie dołączyć do procesu w dowolnym momencie.

### <a name="connection-troubleshooting"></a>Rozwiązywanie problemów z połączeniem

1. Upewnij się, że wybrano **opcję Python remote (ptvsd)** dla **typu połączenia** **(Debugowanie zdalne języka Python** dla **transportu** ze starszymi wersjami).
1. Sprawdź, czy klucz tajny w **docelowych połączeń** (lub **kwalifikator)** dokładnie pasuje do klucza tajnego w kodzie zdalnym.
1. Sprawdź, czy adres IP w **docelowych połączeń** (lub **kwalifikator)** odpowiada adresowi komputera zdalnego.
1. Sprawdź, czy port zdalnego debugowania na komputerze zdalnym został otwarty i czy sufiks portu `:5678`został dołączony do obiektu docelowego połączenia, na przykład .
    - Jeśli chcesz użyć innego portu, można go `enable_attach` określić `address` w wywołaniu `ptvsd.enable_attach(address = ('0.0.0.0', 8080))`za pomocą argumentu, jak w . W takim przypadku otwórz ten konkretny port w zaporze.
1. Sprawdź, czy wersja ptvsd zainstalowany na komputerze `pip3 list` zdalnym, jak zwraca przez dopasowania, które są używane przez wersję narzędzi Języka Python, którego używasz w programie Visual Studio w poniższej tabeli. W razie potrzeby zaktualizuj ptvsd na komputerze zdalnym.

    | Wersja programu Visual Studio | Narzędzia Python/wersja ptvsd |
    | --- | --- |
    | 2017 15.8 | 4.1.1a9 (debuger starsza: 3.2.1.0) |
    | 2017 15.7 | 4.1.1a1 (debuger starsza: 3.2.1.0) |
    | 2017 15.4, 15.5, 15.6 | 3.2.1.0 |
    | 2017 15.3 | 3.2.0 |
    | 2017 15.2 | 3.1.0 |
    | 2017 15.0, 15.1 | 3.0.0 |
    | 2015 | 2.2.6 |
    | 2013 | 2.2.2 |
    | 2012, 2010 | 2.1 |

## <a name="using-ptvsd-3x"></a>Korzystanie z ptvsd 3.x

Poniższe informacje dotyczą tylko zdalnego debugowania z ptvsd 3.x, który zawiera pewne funkcje, które zostały usunięte w ptvsd 4.x.

1. W pliku ptvsd 3.x `enable_attach` funkcja wymagana do przekazania "klucza tajnego" jako pierwszego argumentu, który ogranicza dostęp do uruchomionego skryptu. Ten klucz tajny należy wprowadzić podczas podłączania zdalnego debugera. Chociaż nie zalecane, można zezwolić `enable_attach(secret=None)`każdemu na łączenie się, używać .

1. Docelowy adres `tcp://<secret>@<ip_address>:5678` URL `<secret>` połączenia to `enable_attach` miejsce, w którym jest ciąg przekazywany w kodzie języka Python.

Domyślnie połączenie z serwerem zdalnego debugowania ptvsd 3.x jest zabezpieczone tylko kluczem tajnym, a wszystkie dane są przekazywane w postaci zwykłego tekstu. Aby uzyskać bezpieczniejsze połączenie, ptvsd 3.x `tcsp` obsługuje protokół SSL przy użyciu protokołu, który można skonfigurować w następujący sposób:

1. Na komputerze zdalnym wygeneruj oddzielny certyfikat z podpisem własnym i pliki kluczy przy użyciu openssl:

    ```command
    openssl req -new -x509 -days 365 -nodes -out cert.cer -keyout cert.key
    ```

    Po wyświetleniu monitu użyj nazwy hosta lub adresu IP (w zależności od tego, którego używasz do nawiązania połączenia) dla **nazwy pospolitej,** gdy zostanie wyświetlony monit openssl.

    (Aby uzyskać dodatkowe informacje, `ssl` zobacz [certyfikaty z podpisem własnym](https://docs.python.org/3/library/ssl.html#self-signed-certificates) w docs modułu Pythona. Należy zauważyć, że polecenie w tych docs generuje tylko jeden plik połączony.)

1. W kodzie zmodyfikuj wywołanie `enable_attach` do `certfile` uwzględnienia i `keyfile` argumenty przy użyciu nazw plików jako `ssl.wrap_socket` wartości (te argumenty mają takie samo znaczenie jak dla standardowej funkcji Języka Python):

    ```python
    ptvsd.enable_attach(secret='my_secret', certfile='cert.cer', keyfile='cert.key')
    ```

    Można również wprowadzić tę samą zmianę w pliku kodu na komputerze lokalnym, ale ponieważ ten kod nie jest faktycznie uruchomiony, nie jest absolutnie konieczne.

1. Uruchom ponownie program Python na komputerze zdalnym, dzięki czemu jest gotowy do debugowania.

1. Zabezpiecz kanał, dodając certyfikat do zaufanego głównego urzędu certyfikacji na komputerze z systemem Windows za pomocą programu Visual Studio:

    1. Skopiuj plik certyfikatu z komputera zdalnego na komputer lokalny.
    1. Otwórz **Panel sterowania** i przejdź do pozycji Narzędzia **administracyjne** > **Zarządzaj certyfikatami komputerowymi**.
    1. W wyświetlonym oknie rozwiń pozycję **Zaufane główne urzędy certyfikacji** po lewej stronie, kliknij prawym przyciskiem myszy pozycję **Certyfikaty**i wybierz polecenie**Importuj** **wszystkie zadania** > .
    1. Przejdź do pliku *cer* skopiowanego z komputera zdalnego i wybierz go, a następnie kliknij okna dialogowe, aby zakończyć importowanie.

1. Powtórz proces dołączania w programie Visual Studio, jak opisano wcześniej, teraz używając `tcps://` jako protokołu dla obiektu **docelowego połączenia** (lub **kwalifikatora).**

    ![Wybieranie zdalnego transportu debugowania za pomocą ssl](media/remote-debugging-qualifier-ssl.png)

1. Program Visual Studio monituje o potencjalne problemy z certyfikatami podczas łączenia się za ich za sprawą. Możesz zignorować ostrzeżenia i kontynuować, ale mimo że kanał jest nadal szyfrowany przed podsłuchiwaniem, może być otwarty na ataki typu man-in-the-middle.

    1. Jeśli poniżej widzisz, że **certyfikat zdalny nie jest zaufany,** oznacza to, że certyfikat nie został poprawnie dodumny do zaufanego głównego urzędu certyfikacji. Sprawdź te kroki i spróbuj ponownie.

        ![Ostrzeżenie o zaufanie certyfikatu SSL](media/remote-debugging-ssl-warning.png)

    1. Jeśli poniżej zostanie wyświetlone ostrzeżenie o **zdalnej nazwie certyfikatu,** oznacza to, że podczas tworzenia certyfikatu nie używasz właściwej nazwy hosta lub adresu IP jako **nazwy pospolitej.**

        ![Ostrzeżenie o nazwach hosta certyfikatu SSL](media/remote-debugging-ssl-warning2.png)
