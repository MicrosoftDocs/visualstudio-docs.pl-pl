---
title: Debugowanie kodu w języku Python na komputerach zdalnych systemu Linux
description: Debugowanie kodu w języku Python uruchomiona na zdalnym komputerów z systemem Linux, w tym wymagane kroki konfiguracji, zabezpieczeń i rozwiązywanie problemów przy użyciu programu Visual Studio.
ms.date: 12/06/2018
ms.topic: conceptual
author: kraigb
ms.author: kraigb
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: bb98a94e60d84fc48078be396e0fb48dd8952c55
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55945745"
---
# <a name="remotely-debug-python-code-on-linux"></a>Zdalne debugowanie kodu w języku Python w systemie Linux

Visual Studio można uruchomić i debugowanie lokalne i zdalne aplikacje języka Python na komputerze Windows (zobacz [zdalne debugowanie](../debugger/remote-debugging.md)). Można również debugować zdalnie na różnych systemów operacyjnych, urządzenia lub implementacji języka Python innych niż z użyciem języka CPython [biblioteki ptvsd](https://pypi.python.org/pypi/ptvsd).

Korzystając z ptvsd, debugowanego kodu w języku Python hostuje serwer debugowania, do którego można dołączyć programu Visual Studio. Ta hostingu wymaga niewielkiej modyfikacji w kodzie, aby zaimportować i włączyć serwer i mogą wymagać sieci lub zapory konfiguracji na komputerze zdalnym, aby zezwolić na połączenia TCP.

|   |   |
|---|---|
| ![Ikona aparatu film wideo](../install/media/video-icon.png "Obejrzyj klip wideo") | Wprowadzenie do zdalnego debugowania, zobacz [szczegółowe informacje: Zdalne debugowanie dla platform](https://youtu.be/y1Qq7BrV6Cc) (witrynie youtube.com, 6m22s), która ma zastosowanie do programu Visual Studio 2015 i 2017. |

## <a name="set-up-a-linux-computer"></a>Konfigurowanie komputera z systemem Linux

Do wykonania tego instruktażu potrzebne są następujące elementy:

- Komputera zdalnego z systemem języka Python w systemie operacyjnym, takich jak Mac OS x lub Linux.
- Port 5678 (przychodzące) otwarty w zaporze na tym komputerze, co jest ustawieniem domyślnym dla zdalnego debugowania.

Możesz łatwo tworzyć [maszyny wirtualnej systemu Linux na platformie Azure](/azure/virtual-machines/linux/creation-choices) i [dostęp do niego przy użyciu pulpitu zdalnego](/azure/virtual-machines/linux/use-remote-desktop) z Windows. Ubuntu dla maszyny Wirtualnej jest wygodne, ponieważ język Python jest instalowany domyślnie; w przeciwnym razie zobacz listę w [interpreter języka Python wybranym](installing-python-interpreters.md) dla dodatkowych Python można pobrać architekturę.

Aby uzyskać więcej informacji na temat tworzenia reguł zapory na Maszynie wirtualnej platformy Azure, zobacz [Otwieranie portów dla maszyny Wirtualnej na platformie Azure przy użyciu witryny Azure portal](/azure/virtual-machines/windows/nsg-quickstart-portal).

## <a name="prepare-the-script-for-debugging"></a>Przygotowywanie skryptu do debugowania

1. Na komputerze zdalnym, Utwórz plik w języku Python o nazwie *zgadywania game.py* następującym kodem:

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

1. Zainstaluj `ptvsd` pakietu w Twoim środowisku za pomocą `pip3 install ptvsd`.
   >[!NOTE]
   >To dobry pomysł, aby zarejestrować wersji ptvsd zainstalowanego w przypadku, gdy będą potrzebne do rozwiązywania problemów; [listy ptvsd](https://pypi.python.org/pypi/ptvsd) pokazuje również dostępnych wersji.

1. Włączanie debugowania zdalnego, dodając poniższy kod Najwcześniejsza możliwe w momencie *zgadywania game.py*, przed uruchomieniem innego kodu. (Jednak ściśle wymagane, nie można debugować żadnych wątków w tle zduplikowany przed `enable_attach` funkcja jest wywoływana.)

   ```python
   import ptvsd
   ptvsd.enable_attach()
   ```

1. Zapisz plik i uruchom `python3 guessing-game.py`. Wywołanie `enable_attach` działa w tle, a następnie czeka na połączenia przychodzące, podczas pracy z programem. Jeśli to konieczne, `wait_for_attach` funkcja może zostać wywołana po `enable_attach` blokowania program, dopóki nie dołącza debuger.

> [!Tip]
> Oprócz `enable_attach` i `wait_for_attach`, ptvsd udostępnia również funkcję Pomocnika `break_into_debugger`, który służy jako programowy punkt przerwania, jeśli jest dołączony debuger. Istnieje również `is_attached` funkcja, która zwraca `True` Jeśli jest dołączony debuger (należy pamiętać, że nie ma potrzeby do sprawdzenia tego wyniku przed wywołaniem innych `ptvsd` funkcji).

## <a name="attach-remotely-from-python-tools"></a>Dołącz zdalnie z poziomu narzędzi języka Python

W tych krokach możemy ustawić prosty punkt przerwania, aby zatrzymać proces zdalny.

1. Utwórz kopię pliku zdalnego na komputerze lokalnym, a następnie otwórz go w programie Visual Studio. Nie ma znaczenia, gdzie znajduje się plik, ale jego nazwa powinna odpowiadać nazwie skryptu na komputerze zdalnym.

1. (Opcjonalnie) Aby technologia IntelliSense dla ptvsd na komputerze lokalnym, należy zainstalować pakiet ptvsd w środowisku Python.

1. Wybierz **debugowania** > **dołączyć do procesu**.

1. W **dołączyć do procesu** wyświetlonym oknie dialogowym Ustaw **typu połączenia** do **zdalnego języka Python (ptvsd)**. (W starszych wersjach programu Visual Studio o nazwie tych poleceń **transportu** i **zdalnego debugowania w języku Python**.)

1. W **adres docelowy połączenia** pola (**kwalifikator** w starszych wersjach), wprowadź `tcp://<ip_address>:5678` gdzie `<ip_address>` jest fakt, że komputera zdalnego (która może być jawne adres lub nazwę, np. myvm.cloudapp.NET) i `:5678` zdalnego debugowania numer portu to.

1. Naciśnij klawisz **Enter** do wypełnienia listy ptvsd dostępne procesy na tym komputerze:

    ![Wprowadź adres docelowy połączenia i wyświetlanie listy procesów](media/remote-debugging-qualifier.png)

    Jeśli się zdarzyć, aby uruchomić inny program na komputerze zdalnym po wypełnieniu tej listy, wybierz **Odśwież** przycisku.

1. Wybierz proces do debugowania i następnie **Dołącz**, lub kliknij dwukrotnie ten proces.

1. Program Visual Studio następnie przełącza w trybie debugowania, nadal skrypt do uruchomienia na komputerze zdalnym, zapewniając wszystkie zwykle [debugowania](debugging-python-in-visual-studio.md) możliwości. Na przykład ustaw punkt przerwania na `if guess < number:` wiersza, a następnie przełączyć się do komputera zdalnego i wprowadź inny wynik. Możesz to zrobić, programu Visual Studio w Twojej zatrzymuje komputera lokalnego, w tym punkcie przerwania, aby zobaczyć zmienne lokalne i tak dalej:

    ![Program Visual Studio zatrzymuje debugowanie po trafieniu punktu przerwania](media/remote-debugging-breakpoint-hit.png)

1. Po zatrzymaniu debugowania, Visual Studio odłącza się od programu, który będzie działać na komputerze zdalnym. ptvsd nadal nasłuchuje dołączanie debugery, dzięki czemu możesz dołączyć do procesu w dowolnym momencie ponownie.

### <a name="connection-troubleshooting"></a>Rozwiązywanie problemów z połączeniem

1. Upewnij się, że wybrano **zdalnego języka Python (ptvsd)** dla **typu połączenia** (**zdalnego debugowania w języku Python** dla **transportu** z starsze wersje.)
1. Sprawdź, czy klucz tajny w **adres docelowy połączenia** (lub **kwalifikator**) dokładnie pasuje do wpisu tajnego w kodzie zdalnego.
1. Upewnij się, że adres IP w **adres docelowy połączenia** (lub **kwalifikator**) jest zgodna z komputera zdalnego.
1. Sprawdź otwarciu portu debugowania zdalnego na komputerze zdalnym i że zostały dołączone sufiks portu w element docelowy połączenia, takich jak `:5678`.
    - Jeśli potrzebujesz użyć innego portu, można je było wprowadzić w `enable_attach` wywołać za pomocą `address` argumentu, jak `ptvsd.enable_attach(address = ('0.0.0.0', 8080))`. W tym wypadku Otwórz określonego portu w zaporze.
1. Upewnij się, że wersja ptvsd zainstalowane na komputerze zdalnym, zwrócone przez `pip3 list` pasuje do używanej przez wersję narzędzi Python tools używane w programie Visual Studio w poniższej tabeli. W razie potrzeby zaktualizuj ptvsd na komputerze zdalnym.

    | Visual Studio w wersji | Wersja narzędzi/ptvsd języka Python |
    | --- | --- |
    | 2017 15.8 | 4.1.1a9 (debuger starszej wersji: 3.2.1.0) |
    | 2017 wersji 15.7 | 4.1.1a1 (debuger starszej wersji: 3.2.1.0) |
    | 2017 15.4, 15.5, wersji 15.6 | 3.2.1.0 |
    | 2017 15.3 | 3.2.0 |
    | 2017 15.2 | 3.1.0 |
    | 2017 15.0, 15.1 | 3.0.0 |
    | 2015 | 2.2.6 |
    | 2013 | 2.2.2 |
    | 2012, 2010 | 2.1 |

## <a name="using-ptvsd-3x"></a>Za pomocą ptvsd 3.x

Poniższe informacje dotyczą tylko do debugowania zdalnego z ptvsd 3.x, który zawiera niektóre funkcje, które zostały usunięte w ptvsd 4.x.

1. Za pomocą ptvsd 3.x, `enable_attach` funkcji wymaganych do przekazania "wpis tajny" jako pierwszy argument, który ogranicza dostęp do działającego skryptu. Możesz wprowadzić ten wpis tajny podczas dołączania debugera zdalnego. Chociaż nie jest to zalecane, można zezwolić wszystkim użytkownikom połączyć, użyj `enable_attach(secret=None)`.

1. Adres docelowy połączenia jest adres URL `tcp://<secret>@<ip_address>:5678` gdzie `<secret>` jest przekazany ciąg `enable_attach` w kodzie języka Python.

Domyślnie połączenie z serwerem zdalnego debugowania 3.x ptvsd jest chroniony tylko przez klucz tajny, a wszystkie dane są przekazywane w postaci zwykłego tekstu. W przypadku bardziej bezpieczne połączenia ptvsd 3.x obsługuje przy użyciu protokołu SSL `tcsp` protokołu, który ustawia się w następujący sposób:

1. Na komputerze zdalnym Wygeneruj oddzielny certyfikat z podpisem własnym i plików kluczy przy użyciu biblioteki openssl:

    ```command
    openssl req -new -x509 -days 365 -nodes -out cert.cer -keyout cert.key
    ```

    Po wyświetleniu monitu użyj nazwę hosta lub adres IP (zależności możesz użyć do łączenia z), aby uzyskać **nazwa pospolita** po wyświetleniu monitu przez openssl.

    (Zobacz [certyfikaty z podpisem własnym](https://docs.python.org/3/library/ssl.html#self-signed-certificates) w języku Python `ssl` docs modułu, aby uzyskać więcej informacji. Należy pamiętać, że polecenia w dokumentacji tych generuje tylko jednego połączonego pliku.)

1. W kodzie, zmodyfikuj wywołanie `enable_attach` obejmujący `certfile` i `keyfile` argumentów za pomocą nazwy plików jako wartości (te argumenty mają takie samo znaczenie jak w przypadku standardowych `ssl.wrap_socket` funkce Pythonu):

    ```python
    ptvsd.enable_attach(secret='my_secret', certfile='cert.cer', keyfile='cert.key')
    ```

    Można również wprowadzić tę samą zmianę w pliku kodu na komputerze lokalnym, ale ponieważ ten kod nie jest uruchamiany, nie jest bezwzględnie konieczne.

1. Uruchom ponownie program Python na komputerze zdalnym, dzięki czemu jest gotowy do debugowania.

1. Przez dodawanie certyfikatu do zaufanego głównego urzędu certyfikacji na komputerze Windows z programem Visual Studio, należy zabezpieczyć kanał:

    1. Skopiuj plik certyfikatu z komputera zdalnego na komputerze lokalnym.
    1. Otwórz **Panelu sterowania** i przejdź do **narzędzia administracyjne** > **zarządzania certyfikatami komputera**.
    1. W wyświetlonym oknie rozwiń **zaufane główne urzędy certyfikacji** po lewej stronie, kliknij prawym przyciskiem myszy **certyfikaty**i wybierz **wszystkie zadania**  >  **Importu**.
    1. Przejdź do, a następnie wybierz pozycję *cer* skopiować pliku z komputera zdalnego, kliknij przycisk za pomocą okien dialogowych, aby ukończyć importowanie.

1. Powtórz ten proces dołączania w programie Visual Studio opisany wcześniej, teraz, używając `tcps://` jako protokół dla **adres docelowy połączenia** (lub **kwalifikator**).

    ![Wybieranie transportu debugowania zdalnego przy użyciu protokołu SSL](media/remote-debugging-qualifier-ssl.png)

1. Visual Studio wyświetli monit o potencjalnych problemów z certyfikatami, podczas nawiązywania połączenia za pośrednictwem protokołu SSL. Można zignorować te ostrzeżenia i kontynuować, ale mimo że nadal szyfrowany kanał przed podsłuchiwaniem może być otwarty na ataki typu man-in--middle.

    1. Jeśli widzisz **certyfikatu zdalnego nie jest zaufany** ostrzeżenie poniżej, oznacza to, nie został poprawnie dodany certyfikatów do zaufanego głównego urzędu certyfikacji. Te kroki i spróbuj ponownie.

        ![Ostrzeżenie zaufany certyfikat SSL](media/remote-debugging-ssl-warning.png)

    1. Jeśli widzisz **certyfikatu zdalnego nazwa jest niezgodna z nazwą hosta** ostrzeżenie poniżej, oznacza to, nie używasz prawidłowego hosta lub adres IP jako **nazwa pospolita** podczas tworzenia certyfikatu.

        ![Ostrzeżenie nazwa hosta certyfikatu SSL](media/remote-debugging-ssl-warning2.png)
