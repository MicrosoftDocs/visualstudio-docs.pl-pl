---
title: Wyłączanie dpi-awareness w programie Visual Studio
description: W tym artykule omówiono ograniczenia programu Windows Forms Designer na monitorach HDPI i jak uruchomić program Visual Studio jako proces niewiedzy o dpi.
ms.date: 04/05/2019
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.topic: conceptual
ms.openlocfilehash: 8e7a5a5871b66fd388d7c5a9f774a22163d06729
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75589568"
---
# <a name="disable-dpi-awareness-in-visual-studio"></a>Wyłączanie dpi-awareness w programie Visual Studio

Visual Studio jest aplikacja obsługujących kropki na cal (DPI), co oznacza, że wyświetlanie jest skalowane automatycznie. Jeśli aplikacja syda, że nie jest obsługujących DPI, system operacyjny skaluje aplikację jako mapę bitową. To zachowanie jest również nazywane wirtualizacji DPI. Aplikacja nadal uważa, że działa w 100% skalowanie lub 96 dpi.

W tym artykule omówiono ograniczenia programu Windows Forms Designer na monitorach HDPI i jak uruchomić program Visual Studio jako proces niewiedzy o dpi.

## <a name="windows-forms-designer-on-hdpi-monitors"></a>Projektant formularzy systemu Windows na monitorach HDPI

Projektant **formularzy systemu Windows** w programie Visual Studio nie ma obsługi skalowania. Powoduje to problemy z wyświetlaniem podczas otwierania niektórych formularzy w **programie Windows Forms Designer** na monitorach hdpi (HDPI) o wysokich krokach na cal. Na przykład formanty mogą się nakładać, jak pokazano na poniższej ilustracji:

![Projektant formularzy systemu Windows na monitorze HDPI](./media/win-forms-designer-hdpi.png)

Po otwarciu formularza w **projektancie formularzy systemu Windows** w programie Visual Studio na monitorze HDPI program Visual Studio wyświetla żółty pasek informacyjny u góry projektanta:

![Pasek informacyjny w programie Visual Studio do ponownego uruchomienia w trybie nieświadomym DPI](./media/scaling-gold-bar.png)

Komunikat wywieszono **skalowanie na ekranie głównym jest ustawiona na 200% (192 dpi). Może to spowodować problemy z renderowaniem w oknie projektanta.**

> [!NOTE]
> Ten pasek informacyjny został wprowadzony w programie Visual Studio 2017 w wersji 15.8.

Jeśli nie pracujesz w projektancie i nie musisz dostosowywać układu formularza, możesz zignorować pasek informacyjny i kontynuować pracę w edytorze kodu lub w innych typach projektantów. (Można również [wyłączyć powiadomienia,](#disable-notifications) aby pasek informacyjny nie był nadal wyświetlany). Dotyczy to tylko **projektanta formularzy systemu Windows.** Jeśli potrzebujesz pracy w **projektancie formularzy systemu Windows,** następna sekcja pomaga [rozwiązać problem](#to-resolve-the-display-problem).

## <a name="to-resolve-the-display-problem"></a>Aby rozwiązać problem z wyświetlaniem

Istnieją trzy opcje rozwiązania problemu z wyświetlaniem:

- [Uruchom ponownie program Visual Studio jako proces nieświadomy dpi](#restart-visual-studio-as-a-dpi-unaware-process)
- [Dodawanie wpisu rejestru](#add-a-registry-entry)
- [Ustaw ustawienie skalowania wyświetlania na 100%](#set-your-display-scaling-setting-to-100)

### <a name="restart-visual-studio-as-a-dpi-unaware-process"></a>Uruchom ponownie program Visual Studio jako proces nieświadomy dpi

Program Visual Studio można ponownie uruchomić jako proces nieświadomy DPI, wybierając opcję na żółtym pasku informacyjnym. Jest to preferowany sposób rozwiązania problemu.

Gdy program Visual Studio działa jako proces nieświadomy DPI, problemy z układem projektanta są rozwiązywane, ale czcionki mogą być rozmyte. Visual Studio wyświetla inny żółty komunikat informacyjny, gdy jest uruchamiany jako proces nieświadomy DPI, który mówi, że **visual studio jest uruchomiony jako proces nieświadomy DPI. Projektanci WPF I XAML mogą nie wyświetlać poprawnie.** Pasek informacyjny udostępnia również opcję **ponownego uruchomienia programu Visual Studio jako procesu obsługującego dpi.**

> [!NOTE]
> - Jeśli zostały oddokowane okna narzędzi w programie Visual Studio po wybraniu opcji ponownego uruchomienia jako proces nierozważny DPI, położenie tych okien narzędzia może ulec zmianie.
> - Jeśli używasz domyślnego profilu języka Visual Basic lub jeśli masz opcję **Zapisz nowe projekty po utworzeniu,** która**Options** > została odznaczona w **opcjach narzędziOwych** > **projektów i rozwiązań,** program Visual Studio nie może ponownie otworzyć projektu po ponownym uruchomieniu jako proces nieświadomy dpi. Można jednak otworzyć projekt, wybierając go w obszarze **Pliki** > **ostatnich projektów i rozwiązań**.

Ważne jest ponowne uruchomienie programu Visual Studio jako procesu obsługującego dpi po zakończeniu pracy w **programie Windows Forms Designer.** Gdy jest uruchomiony jako proces nieświadomy DPI, czcionki mogą wyglądać rozmazane i mogą pojawić się problemy w innych projektantów, takich jak **Projektant XAML**. Jeśli zamkniesz i ponownie otworzysz program Visual Studio, gdy jest uruchomiony w trybie nieświadomym DPI, staje się dpi-aware ponownie. Można również kliknąć opcję Uruchom ponownie program Visual Studio jako opcję **procesu obsługującego dpi** na pasku informacyjnym.

### <a name="add-a-registry-entry"></a>Dodawanie wpisu rejestru

Program Visual Studio można oznaczyć jako dpi-unaware, modyfikując rejestr. Otwórz **Edytor rejestru** i dodaj wpis do podklucza **HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows NT\CurrentVersion\AppCompatFlags\Layers:**

**Wpis:** W zależności od tego, czy używasz programu Visual Studio 2017 czy 2019, użyj jednej z następujących wartości:

- C:\Pliki programów (x86)\Microsoft Visual Studio\2017\Społeczność\Common7\IDE\devenv.exe
- C:\Pliki programów (x86)\Microsoft Visual Studio\2019\Społeczność\Common7\IDE\devenv.exe

> [!NOTE]
> Jeśli używasz wersji Professional lub Enterprise programu Visual Studio, zastąp **społeczność** **professional** lub **enterprise** we wpisie. W razie potrzeby należy również wymienić literę napędu.

**Typ**: REG_SZ

**Wartość**: DPIUNAWARE

> [!NOTE]
> Visual Studio pozostaje w trybie dpi-unaware do momentu usunięcia wpisu rejestru.

### <a name="set-your-display-scaling-setting-to-100"></a>Ustaw ustawienie skalowania wyświetlania na 100%

Aby ustawić ustawienie skalowania wyświetlania na 100% w systemie Windows 10, wpisz **ustawienia wyświetlania** w polu wyszukiwania paska zadań, a następnie wybierz pozycję **Zmień ustawienia wyświetlania**. W oknie **Ustawienia** ustaw **rozmiar tekstu, aplikacji i innych elementów** na **100%**.

Ustawienie skalowania ekranu na 100% może być niepożądane, ponieważ może sprawić, że interfejs użytkownika będzie zbyt mały, aby można było go użyć.

## <a name="disable-notifications"></a>Wyłączanie powiadomień

Można wybrać, aby nie otrzymywać powiadomionych o problemach ze skalowaniem DPI w programie Visual Studio. Możesz wyłączyć powiadomienia, jeśli nie pracujesz w projektancie, na przykład.

Aby wyłączyć powiadomienia, wybierz pozycję**Opcje** **narzędzi,** > aby otworzyć okno dialogowe **Opcje.** Następnie wybierz pozycję **Windows Forms Designer** > **General**i ustaw **powiadomienia skalowania DPI** na **False**.

![Opcja skalowania dpi w programie Visual Studio](./media/notifications-option.png)

Jeśli chcesz później ponownie konfigurować powiadomienia skalowania, ustaw właściwość na **True**.

## <a name="troubleshoot"></a>Rozwiązywanie problemów

Jeśli przejście świadomości DPI nie działa zgodnie z oczekiwaniami w programie Visual `dpiAwareness` Studio, sprawdź, czy wartość jest **w HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image File Execution Options\devenv.exe** w Edytorze rejestru. Usuń wartość, jeśli jest obecna.

## <a name="see-also"></a>Zobacz też

- [Automatyczne skalowanie w formularzach systemu Windows](/dotnet/framework/winforms/automatic-scaling-in-windows-forms)
