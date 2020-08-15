---
title: Debugowanie kodu w języku Python na komputerach zdalnych z systemem Linux
description: Program Visual Studio umożliwia debugowanie kodu w języku Python uruchomionego na komputerach zdalnych z systemem Linux, w tym niezbędnych kroków konfiguracji, zabezpieczenia i rozwiązywanie problemów.
ms.date: 12/06/2018
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.custom: seodec18
ms.workload:
- python
- data-science
ms.openlocfilehash: a1f8c145d7c9c072adcc902cae9f2b6ae36937cd
ms.sourcegitcommit: d8609a78b460d4783f5d59c0c89454910a4dbd21
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/14/2020
ms.locfileid: "88246342"
---
Program Visual Studio może uruchamiać i debugować aplikacje języka Python lokalnie i zdalnie na komputerze z systemem Windows (zobacz [debugowanie zdalne](../../../debugger/remote-debugging.md)). Może on również debugować zdalnie w innym systemie operacyjnym, urządzeniu lub implementacji języka Python innym niż CPython za pomocą [biblioteki ptvsd](https://pypi.python.org/pypi/ptvsd).

W przypadku korzystania z ptvsd kod języka Python jest debugowany na serwerze debugowania, do którego można dołączyć Visual Studio. Hosting ten wymaga niewielkiej modyfikacji kodu w celu zaimportowania i włączenia serwera i może wymagać konfiguracji sieci lub zapory na komputerze zdalnym, aby zezwolić na połączenia TCP.

![ikona aparatu filmu wideo](../../../install/media/video-icon.png "Obejrzyj film") Aby zapoznać się z wprowadzeniem do zdalnego debugowania, zobacz [szczegółowe szczegółowe: Międzyplatformowe debugowanie zdalne](https://youtu.be/y1Qq7BrV6Cc) (YouTube.com, 6m22s), które ma zastosowanie zarówno dla programu Visual Studio 2015, jak i 2017.

## <a name="set-up-a-linux-computer"></a>Konfigurowanie komputera z systemem Linux

Następujące elementy są konieczne do wykonania tego przewodnika:

- Komputer zdalny z systemem Python w systemie operacyjnym, takim jak Mac OSX lub Linux.
- Port 5678 (przychodzący) został otwarty na zaporze tego komputera, co jest ustawieniem domyślnym dla zdalnego debugowania.

Możesz łatwo utworzyć [maszynę wirtualną z systemem Linux na platformie Azure](/azure/virtual-machines/linux/creation-choices) i [uzyskać do niej dostęp za pomocą pulpit zdalny](/azure/virtual-machines/linux/use-remote-desktop) z systemu Windows. Ubuntu dla maszyny wirtualnej jest wygodne, ponieważ język Python jest instalowany domyślnie. w przeciwnym razie zapoznaj się z listą dotyczącą [instalacji interpretera języka Python](../../installing-python-interpreters.md) w przypadku dodatkowych lokalizacji pobierania w języku Python.

Aby uzyskać szczegółowe informacje na temat tworzenia reguły zapory dla maszyny wirtualnej platformy Azure, zobacz [otwieranie portów do maszyny wirtualnej na platformie Azure przy użyciu Azure Portal](/azure/virtual-machines/windows/nsg-quickstart-portal).

## <a name="prepare-the-script-for-debugging"></a>Przygotuj skrypt do debugowania

1. Na komputerze zdalnym Utwórz plik w języku Python o nazwie *guessing-game.py* przy użyciu następującego kodu:

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

1. Zainstaluj `ptvsd` pakiet w środowisku przy użyciu programu `pip3 install ptvsd` .
   >[!NOTE]
   >Dobrym pomysłem jest zarejestrowanie wersji ptvsd, która jest zainstalowana na wypadek, gdyby była potrzebna do rozwiązywania problemów. [Lista ptvsd](https://pypi.python.org/pypi/ptvsd) zawiera również dostępne wersje.

1. Włącz debugowanie zdalne, dodając Poniższy kod w najwcześniejszym możliwym miejscu w *guessing-game.py*przed innym kodem. (Chociaż nie jest to rygorystyczne wymaganie, nie jest możliwe debugowanie wszystkich wątków w tle zduplikowanych przed `enable_attach` wywołaniem funkcji).

   ```python
   import ptvsd
   ptvsd.enable_attach()
   ```

1. Zapisz plik i uruchom go `python3 guessing-game.py` . Wywołanie do `enable_attach` uruchomienia w tle i czeka na połączenia przychodzące, gdy w przeciwnym razie nie będzie można korzystać z programu. Jeśli to konieczne, `wait_for_attach` Funkcja może być wywoływana po `enable_attach` zablokowaniu programu do momentu dołączenia debugera.

> [!Tip]
> Oprócz `enable_attach` i `wait_for_attach` , ptvsd również udostępnia funkcję pomocnika `break_into_debugger` , która służy jako programowy punkt przerwania, Jeśli debuger jest dołączony. Istnieje również `is_attached` Funkcja, która zwraca `True` w przypadku podłączenia debugera (należy zauważyć, że nie trzeba sprawdzać tego wyniku przed wywołaniem innych `ptvsd` funkcji).

## <a name="attach-remotely-from-python-tools"></a>Dołącz zdalnie z narzędzi Python

W tych krokach ustawimy prosty punkt przerwania, aby zatrzymać proces zdalny.

1. Utwórz kopię pliku zdalnego na komputerze lokalnym i otwórz go w programie Visual Studio. Nie ma znaczenia, gdzie znajduje się plik, ale jego nazwa powinna być zgodna z nazwą skryptu na komputerze zdalnym.

1. Obowiązkowe Aby można było korzystać z funkcji IntelliSense dla ptvsd na komputerze lokalnym, należy zainstalować pakiet ptvsd w środowisku języka Python.

1. Wybierz pozycję **Debuguj**  >  **Dołącz do procesu**.

1. W wyświetlonym oknie dialogowym **Dołącz do procesu** ustaw opcję **Typ połączenia** na **zdalne środowisko Python (ptvsd)**. (W starszych wersjach programu Visual Studio są to następujące polecenia o nazwie **transport** i **debugowanie zdalne**w języku Python).

1. W polu **cel połączenia** (**kwalifikator** we wcześniejszych wersjach) wprowadź `tcp://<ip_address>:5678` miejsce, gdzie jest to `<ip_address>` komputer zdalny (może to być jawny adres lub nazwa, taka jak MyVM.cloudapp.NET), i `:5678` jest numerem portu zdalnego debugowania.

1. Naciśnij klawisz **Enter** , aby wypełnić listę dostępnych procesów ptvsd na tym komputerze:

    ![Wprowadzanie elementu docelowego połączenia i wyświetlanie listy procesów](../../media/remote-debugging-qualifier.png)

    W przypadku uruchomienia na komputerze zdalnym innego programu po wypełnieniu tej listy wybierz przycisk **Odśwież** .

1. Wybierz proces do debugowania, a następnie **Dołącz**lub kliknij dwukrotnie proces.

1. Program Visual Studio przełączy się w tryb debugowania, podczas gdy skrypt nadal jest uruchamiany na komputerze zdalnym, zapewniając wszystkie normalne możliwości [debugowania](../../debugging-python-in-visual-studio.md) . Na przykład można ustawić punkt przerwania w `if guess < number:` wierszu, a następnie przełączyć się na komputer zdalny i wprowadzić kolejną próbkę. Po wykonaniu tej czynności program Visual Studio na komputerze lokalnym przestaje działać w tym punkcie przerwania, zawiera zmienne lokalne i tak dalej:

    ![Program Visual Studio wstrzymuje debugowanie po trafieniu punktu przerwania](../../media/remote-debugging-breakpoint-hit.png)

1. Po zatrzymaniu debugowania program Visual Studio odłącza się od programu, który jest nadal uruchamiany na komputerze zdalnym. ptvsd również kontynuuje nasłuchiwanie w celu dołączenia debugerów, aby można było ponownie dołączyć do procesu w dowolnym momencie.

### <a name="connection-troubleshooting"></a>Rozwiązywanie problemów z połączeniem

1. Upewnij się, że wybrano element **Python Remote (ptvsd)** dla **typu połączenia** (**debugowanie zdalne** w języku Python dla **transportu** ze starszymi wersjami).
1. Sprawdź, czy klucz tajny w **miejscu docelowym połączenia** (lub **kwalifikator**) dokładnie pasuje do wpisu tajnego w kodzie zdalnym.
1. Sprawdź, czy adres IP w **miejscu docelowym połączenia** (lub **kwalifikator**) jest zgodny z komputerem zdalnym.
1. Sprawdź, czy na komputerze zdalnym został otwarty port debugowania zdalnego i czy został dołączony sufiks portu w miejscu docelowym połączenia, na przykład `:5678` .
    - Jeśli musisz użyć innego portu, możesz określić go w `enable_attach` wywołaniu przy użyciu `address` argumentu, jak w `ptvsd.enable_attach(address = ('0.0.0.0', 8080))` . W takim przypadku należy otworzyć określony port w zaporze.
1. Sprawdź, czy wersja programu ptvsd zainstalowana na komputerze zdalnym została zwrócona przez `pip3 list` dopasowania używane przez wersję narzędzi języka Python, których używasz w programie Visual Studio, w poniższej tabeli. W razie potrzeby zaktualizuj ptvsd na komputerze zdalnym.

    | Wersja programu Visual Studio | Narzędzia Python/wersja ptvsd |
    | --- | --- |
    | 2017 15,8 | 4.1.1 A9 (starszy debuger: 3.2.1.0) |
    | 2017 15,7 | 4.1.1 a1 (starszy debuger: 3.2.1.0) |
    | 2017 15,4, 15,5, 15,6 | 3.2.1.0 |
    | 2017 15,3 | 3.2.0 |
    | 2017 15,2 | 3.1.0 |
    | 2017 15,0, 15,1 | 3.0.0 |
    | 2015 | 2.2.6 |
    | 2013 | 2.2.2 |
    | 2012, 2010 | 2.1 |

## <a name="using-ptvsd-3x"></a>Korzystanie z ptvsd 3. x

Poniższe informacje dotyczą tylko debugowania zdalnego z ptvsd 3. x, które zawiera pewne funkcje, które zostały usunięte w ptvsd 4. x.

1. W ptvsd 3. x `enable_attach` Funkcja wymagana do przekazania "tajnego" jako pierwszego argumentu, który ogranicza dostęp do uruchomionego skryptu. Ten wpis tajny należy wprowadzić podczas dołączania zdalnego debugera. Chociaż nie jest to zalecane, można zezwolić wszystkim użytkownikom na nawiązywanie połączeń, korzystanie z programu `enable_attach(secret=None)` .

1. Docelowy adres URL połączenia to `tcp://<secret>@<ip_address>:5678` `<secret>` , gdzie jest ciągiem przekazaną `enable_attach` w kodzie języka Python.

Domyślnie połączenie z serwerem debugowania zdalnego ptvsd 3. x jest zabezpieczone tylko przez wpis tajny, a wszystkie dane są przesyłane w postaci zwykłego tekstu. Aby zapewnić bezpieczniejsze połączenie, ptvsd 3. x obsługuje protokół SSL przy użyciu `tcsp` protokołu, który można skonfigurować w następujący sposób:

1. Na komputerze zdalnym Wygeneruj oddzielne certyfikaty z podpisem własnym i pliki kluczy przy użyciu OpenSSL:

    ```command
    openssl req -new -x509 -days 365 -nodes -out cert.cer -keyout cert.key
    ```

    Po wyświetleniu monitu użyj nazwy hosta lub adresu IP (w zależności od tego, który jest używany do nawiązania połączenia) w polu **Nazwa pospolita** , gdy zostanie wyświetlony monit OpenSSL

    (Zobacz [certyfikaty z podpisem własnym](https://docs.python.org/3/library/ssl.html#self-signed-certificates) w dokumentacji modułu języka Python, `ssl` Aby uzyskać dodatkowe informacje. Należy zauważyć, że polecenie w tych dokumentach generuje tylko jeden połączony plik.)

1. W kodzie zmodyfikuj wywołanie `enable_attach` do dołączenia do dołączania `certfile` i `keyfile` argumentów przy użyciu nazw plików jako wartości (te argumenty mają takie samo znaczenie jak dla standardowej `ssl.wrap_socket` funkcji języka Python):

    ```python
    ptvsd.enable_attach(secret='my_secret', certfile='cert.cer', keyfile='cert.key')
    ```

    Możesz również wprowadzić tę samą zmianę w pliku kodu na komputerze lokalnym, ale ponieważ ten kod nie jest faktycznie uruchomiony, nie jest to absolutnie konieczne.

1. Uruchom ponownie program Python na komputerze zdalnym, aby przygotować go do debugowania.

1. Zabezpiecz kanał, dodając certyfikat do zaufanego głównego urzędu certyfikacji na komputerze z systemem Windows za pomocą programu Visual Studio:

    1. Skopiuj plik certyfikatu z komputera zdalnego na komputer lokalny.
    1. Otwórz **Panel sterowania** i przejdź do **Narzędzia administracyjne**  >  **Zarządzanie certyfikatami komputerów**.
    1. W wyświetlonym oknie rozwiń węzeł **Zaufane główne** urzędy certyfikacji po lewej stronie, kliknij prawym przyciskiem myszy pozycję **Certyfikaty**, a następnie wybierz pozycję **wszystkie zadania**  >  **Importuj**.
    1. Przejdź do i wybierz plik *CER* skopiowany z komputera zdalnego, a następnie kliknij okna dialogowe, aby zakończyć importowanie.

1. Powtórz proces Attach w programie Visual Studio zgodnie z wcześniejszym opisem, teraz używając `tcps://` jako protokołu dla **celu połączenia** (lub **kwalifikatora**).

    ![Wybieranie transportu zdalnego debugowania przy użyciu protokołu SSL](../../media/remote-debugging-qualifier-ssl.png)

1. Program Visual Studio poprosi o potencjalne problemy z certyfikatami podczas nawiązywania połączenia za pośrednictwem protokołu SSL. Można zignorować ostrzeżenia i przeprowadzić dalsze czynności, ale mimo że kanał jest wciąż szyfrowany przed podsłuchiwaniem, może być otwarty w przypadku ataków typu man-in-the-middle.

    1. Jeśli zobaczysz, że **certyfikat zdalny nie jest zaufany** poniżej, oznacza to, że certyfikat nie został poprawnie dodany do zaufanego głównego urzędu certyfikacji. Sprawdź te kroki i spróbuj ponownie.

        ![Zaufane ostrzeżenie certyfikatu SSL](../../media/remote-debugging-ssl-warning.png)

    1. Jeśli zobaczysz, że **Nazwa certyfikatu zdalnego nie jest zgodna** z ostrzeżeniem nazwy hosta poniżej, oznacza to, że podczas tworzenia certyfikatu nie użyto prawidłowej **nazwy** hosta lub adresu IP.

        ![Ostrzeżenie o nazwie hosta certyfikatu SSL](../../media/remote-debugging-ssl-warning2.png)
