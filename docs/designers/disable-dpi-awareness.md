---
title: Wyłączanie rozpoznawania DPI w programie Visual Studio
description: W tym artykule omówiono ograniczenia Projektant formularzy systemu Windows monitorów HDPI oraz sposób uruchamiania programu Visual Studio jako procesu niezależnego od rozdzielczości DPI.
ms.date: 09/28/2020
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.topic: conceptual
ms.openlocfilehash: 08eb15914ad381fd81a838f5e09a1350bedff4fd
ms.sourcegitcommit: 31f216b5f7491d5558de5b7ea4ebb0eb1faa3b9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/29/2020
ms.locfileid: "91493312"
---
# <a name="disable-dpi-awareness-in-visual-studio"></a>Wyłączanie rozpoznawania DPI w programie Visual Studio

Program Visual Studio to aplikacja obsługująca punkty na cal (DPI), co oznacza, że wyświetlacz automatycznie skaluje się. Jeśli aplikacja nie rozpoznaje rozdzielczości DPI, system operacyjny skaluje aplikację jako mapę bitową. Takie zachowanie jest nazywane również wirtualizacją DPI. Aplikacja nadal uważa, że jest uruchomiona z szybkością 100% skalowania lub 96 dpi.

W tym artykule omówiono ograniczenia Projektant formularzy systemu Windows monitorów HDPI oraz sposób uruchamiania programu Visual Studio jako procesu niezależnego od rozdzielczości DPI.

## <a name="windows-forms-designer-on-hdpi-monitors"></a>Projektant formularzy systemu Windows monitorów HDPI

**Projektant formularzy systemu Windows** w programie Visual Studio nie obsługuje skalowania. Powoduje to wyświetlenie problemów podczas otwierania niektórych formularzy w **Projektant formularzy systemu Windows** na monitorach o wysokiej rozdzielczości na cal (HDPI). Na przykład, kontrolki mogą wydawać się pokrywane, jak pokazano na poniższej ilustracji:

![Projektant formularzy systemu Windows na monitorze HDPI](./media/win-forms-designer-hdpi.png)

Po otwarciu formularza w **Projektant formularzy systemu Windows** w programie Visual Studio na MONITORze HDPI program Visual Studio wyświetli żółty pasek informacyjny w górnej części narzędzia Projektant:

![Pasek informacyjny w programie Visual Studio w celu ponownego uruchomienia w trybie nieświadomej rozdzielczości DPI](./media/scaling-gold-bar.png)

Komunikat o **skalowaniu na ekranie głównym jest ustawiany na 200% (192 dpi). Może to spowodować problemy z renderowaniem w oknie projektanta.**

> [!NOTE]
> Ten pasek informacyjny został wprowadzony w programie Visual Studio 2017 w wersji 15,8.

Jeśli nie Pracujesz w Projektancie i nie musisz regulować układu formularza, możesz zignorować pasek informacyjny i kontynuować pracę w edytorze kodu lub w innych typach projektantów. (Możesz również [wyłączyć powiadomienia](#disable-notifications) , aby pasek informacyjny nadal nie był wyświetlany). Dotyczy tylko **Projektant formularzy systemu Windows** . W przypadku konieczności pracy w **Projektant formularzy systemu Windows**Następna sekcja pomoże [rozwiązać ten problem](#to-resolve-the-display-problem).

## <a name="to-resolve-the-display-problem"></a>Aby rozwiązać problem z wyświetlaniem

Istnieją trzy opcje rozwiązania problemu z wyświetlaniem:

- [Uruchom ponownie program Visual Studio jako proces obsługujący rozdzielczość DPI](#restart-visual-studio-as-a-dpi-unaware-process)
- [Dodawanie wpisu rejestru](#add-a-registry-entry)
- [Ustaw ustawienie skalowania ekranu na 100%](#set-your-display-scaling-setting-to-100)

> [!TIP]
> Jeśli wolisz zarządzać ustawieniami z poziomu wiersza polecenia, [`devenv.exe`](../ide/reference/devenv-command-line-switches.md) przyjmuje `/noscale` jako parametr wiersza polecenia do uruchomienia w trybie skalowania 100%.

### <a name="restart-visual-studio-as-a-dpi-unaware-process"></a>Uruchom ponownie program Visual Studio jako proces obsługujący rozdzielczość DPI

Program Visual Studio można uruchomić ponownie jako proces niezależny od rozdzielczości DPI, wybierając opcję na żółtym pasku informacyjnym. Jest to preferowany sposób rozwiązania problemu.

Gdy program Visual Studio działa jako proces obsługujący rozdzielczości DPI, rozwiązywane są problemy z układem projektanta, ale czcionki mogą wydawać się zamazane. Program Visual Studio Wyświetla inny żółty komunikat informacyjny, gdy działa jako proces, który jest niezależny od rozdzielczości DPI, który mówi, że **program Visual Studio jest uruchomiony jako proces obsługujący rozdzielczości DPI. Projektanci WPF i XAML mogą nie wyświetlać się poprawnie.** Pasek informacyjny udostępnia również opcję **ponownego uruchomienia programu Visual Studio jako procesu obsługującego rozdzielczości DPI**.

> [!NOTE]
> - Jeśli w programie Visual Studio zostały zazadokowane okna narzędzi, w przypadku wybrania opcji ponownego uruchomienia jako procesu niezależnego od rozdzielczości DPI pozycja tych okien narzędzi może się zmienić.
> - Jeśli używasz domyślnego profilu Visual Basic lub jeśli masz opcję **Zapisz nowe projekty po utworzeniu** opcji w obszarze **Narzędzia**  >  **Opcje**  >  **projekty i rozwiązania**, program Visual Studio nie może ponownie otworzyć projektu, gdy zostanie on ponownie uruchomiony jako proces nieobsługujący rozdzielczości DPI. Można jednak otworzyć projekt, wybierając go w obszarze **pliki**  >  **najnowsze projekty i rozwiązania**.

Ważne jest, aby ponownie uruchomić program Visual Studio jako proces obsługujący DPI po zakończeniu pracy w **Projektant formularzy systemu Windows**. Gdy działa jako proces obsługujący rozdzielczości DPI, czcionki mogą wyglądać zamazane i mogą być widoczne problemy w innych projektantach, takich jak **Projektant XAML**. Po zamknięciu i ponownym otwarciu programu Visual Studio, gdy jest on uruchamiany w trybie z obsługą rozdzielczości DPI, będzie on ponownie uwzględniany w rozdzielczości DPI. Możesz również wybrać pozycję **Uruchom ponownie program Visual Studio jako opcję procesu z obsługą rozdzielczości DPI** na pasku informacyjnym.

### <a name="add-a-registry-entry"></a>Dodawanie wpisu rejestru

Program Visual Studio można oznaczyć jako niezależny od rozdzielczości DPI, modyfikując rejestr. Otwórz **Edytor rejestru** i Dodaj wpis do podklucza **HKEY_CURRENT_USER \SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers** :

**Wpis**: w zależności od tego, czy używasz programu Visual Studio 2017 lub 2019, użyj jednej z następujących wartości:

- C:\Program Files (x86) \Microsoft Visual Studio\2017\Community\Common7\IDE\devenv.exe
- C:\Program Files (x86) \Microsoft Visual Studio\2019\Community\Common7\IDE\devenv.exe

> [!NOTE]
> Jeśli korzystasz z wersji Professional lub Enterprise programu Visual Studio, Zastąp **społeczność** z **profesjonalnym** lub **przedsiębiorstwem** we wpisie. W razie potrzeby należy również zastąpić literę dysku.

**Typ**: REG_SZ

**Wartość**: DPIUNAWARE

> [!NOTE]
> Program Visual Studio pozostaje w trybie nieobsługującym rozdzielczości DPI do momentu usunięcia wpisu rejestru.

### <a name="set-your-display-scaling-setting-to-100"></a>Ustaw ustawienie skalowania ekranu na 100%

Aby ustawić ustawienia skalowania wyświetlania na 100% w systemie Windows 10, wpisz **Ustawienia wyświetlania** w polu wyszukiwania paska zadań, a następnie wybierz pozycję **Zmień ustawienia wyświetlania**. W oknie **Ustawienia** ustaw opcję **Zmień rozmiar tekstu, aplikacji i innych elementów** na **100%**.

Ustawienie skalowania ekranu na 100% może być niepożądane, ponieważ może to spowodować, że interfejs użytkownika jest zbyt mały, aby można go było używać.

## <a name="disable-notifications"></a>Wyłącz powiadomienia

Możesz zrezygnować z powiadamiania o problemach z skalowaniem DPI w programie Visual Studio. Możesz chcieć wyłączyć powiadomienia, jeśli nie Pracujesz w projektancie, na przykład.

Aby wyłączyć powiadomienia, wybierz **Tools**  >  **Opcje** narzędzia, aby otworzyć okno dialogowe **Opcje** . Następnie wybierz opcję **Projektant formularzy systemu Windows**  >  **Ogólne**i ustaw **powiadomienia skalowania dpi** na **wartość false**.

![Opcja powiadomień skalowania DPI w programie Visual Studio](./media/notifications-option.png)

Jeśli chcesz później ponownie włączyć powiadomienia dotyczące skalowania, ustaw właściwość na **wartość true**.

## <a name="troubleshoot"></a>Rozwiązywanie problemów

Jeśli przejście rozpoznawania DPI nie działa w oczekiwany sposób w programie Visual Studio, sprawdź, czy w `dpiAwareness` Edytorze rejestru znajduje się wartość w **HKEY_LOCAL_MACHINE \Software\microsoft\windows NT\CurrentVersion\Image wykonywanie pliku Options\devenv.exe** . Usuń wartość, jeśli jest obecna.

## <a name="see-also"></a>Zobacz też

- [Automatyczne skalowanie w Windows Forms](/dotnet/framework/winforms/automatic-scaling-in-windows-forms)
