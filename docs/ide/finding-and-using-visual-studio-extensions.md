---
title: Znajdowanie i instalowanie rozszerzeń
ms.date: 09/18/2019
ms.topic: conceptual
f1_keywords:
- vs.ExtensionManager
helpviewer_keywords:
- install extensions
- install packages
- managing extensions visual studio
ms.assetid: 4ca92d93-31b9-47ef-8109-4a429d9e2ca3
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f016af58b5799ca37b1a8f0cc54366d639c57c03
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75594412"
---
# <a name="manage-extensions-for-visual-studio"></a>Zarządzanie rozszerzeniami dla programu Visual Studio

Rozszerzenia są pakiety kodu, które są uruchamiane wewnątrz programu Visual Studio i zapewniają nowe lub ulepszone funkcje. Rozszerzenia mogą być formantami, przykładami, szablonami, narzędziami lub innymi składnikami, które dodają funkcje do programu Visual Studio, na przykład [udostępnianie na żywo](https://marketplace.visualstudio.com/items?itemName=MS-vsliveshare.vsls-vs) lub program Visual Studio [IntelliCode](https://marketplace.visualstudio.com/items?itemName=VisualStudioExptTeam.VSIntelliCode).

Aby uzyskać informacje dotyczące tworzenia rozszerzeń programu Visual Studio, zobacz [Visual Studio SDK](../extensibility/visual-studio-sdk.md). Aby uzyskać informacje na temat używania rozszerzeń, zobacz stronę poszczególnych rozszerzeń w [programie Visual Studio Marketplace](https://marketplace.visualstudio.com).

::: moniker range="vs-2017"

## <a name="extensions-and-updates-dialog-box"></a>Okno dialogowe Rozszerzenia i aktualizacje

Okno dialogowe **Rozszerzenia i aktualizacje** służy do instalowania rozszerzeń programu Visual Studio i zarządzania nimi. Aby otworzyć okno **dialogowe Rozszerzenia i aktualizacje,** wybierz polecenie**Rozszerzenia i aktualizacje** **narzędzi** > lub wpisz rozszerzenia w polu wyszukiwania Szybkie **uruchamianie.** **Quick Launch**

::: moniker-end

::: moniker range=">=vs-2019"

## <a name="manage-extensions-dialog-box"></a>Okno dialogowe Zarządzanie rozszerzeniami

Okno dialogowe **Zarządzanie rozszerzeniami** służy do instalowania rozszerzeń programu Visual Studio i zarządzania nimi. Aby otworzyć okno dialogowe **Zarządzanie rozszerzeniami,** wybierz polecenie **Zarządzanie rozszerzeniami** > **Manage Extensions**. Możesz też **wpisać rozszerzenia** w polu wyszukiwania i wybrać pozycję **Zarządzaj rozszerzeniami**.

::: moniker-end

![Okno Rozszerzenia w programie Visual Studio](media/finding-using-visual-studio-extensions/extensions-and-updates.png)

Okienko po lewej stronie kategoryzuje rozszerzenia według tych, które są zainstalowane, te dostępne w programie Visual Studio Marketplace **(Online)** i te, które mają dostępne aktualizacje. **Menedżer rozszerzeń mobilnych** przechowuje listę wszystkich rozszerzeń programu Visual Studio zainstalowanych na dowolnym komputerze lub wystąpieniu programu Visual Studio. Został zaprojektowany, aby ułatwić znajdowanie ulubionych rozszerzeń.

## <a name="find-and-install-extensions"></a>Znajdowanie i instalowanie rozszerzeń

::: moniker range="vs-2017"

Rozszerzenia można zainstalować z [programu Visual Studio Marketplace](https://marketplace.visualstudio.com) lub okna dialogowego Rozszerzenia i aktualizacje w programie Visual Studio.

Aby zainstalować rozszerzenia z poziomu programu Visual Studio:

1. W **menu Rozszerzenia** > **i aktualizacje**narzędzi znajdź rozszerzenie, które chcesz zainstalować. Jeśli znasz nazwę lub część nazwy rozszerzenia, możesz wyszukać w oknie **wyszukiwania.**

2. Wybierz przycisk **Download** (Pobierz).

   Rozszerzenie jest zaplanowane do zainstalowania. Twoje rozszerzenie zostanie zainstalowane po zamknięciu wszystkich wystąpień programu Visual Studio.

Podczas próby instalacji rozszerzenia, które ma zależności, instalator sprawdza, czy są one już zainstalowane. Jeśli nie są zainstalowane, w oknie dialogowym **Rozszerzenia i aktualizacje** wymieniono zależności, które muszą zostać zainstalowane przed zainstalowaniem rozszerzenia.

### <a name="install-without-using-the-extensions-and-updates-dialog-box"></a>Instalowanie bez korzystania z okna dialogowego Rozszerzenia i aktualizacje

Rozszerzenia, które zostały spakowane w plikach *vsix* mogą być dostępne w lokalizacjach innych niż Visual Studio Marketplace. Okno**dialogowe Rozszerzenia i aktualizacje** **narzędzi** > nie może wykryć tych plików, ale można zainstalować plik *vsix,* klikając dwukrotnie plik lub wybierając plik i naciskając klawisz **Enter**. Następnie postępuj zgodnie z instrukcjami. Po zainstalowaniu rozszerzenia można użyć okna dialogowego **Rozszerzenia i aktualizacje,** aby je włączyć, wyłączyć lub odinstalować.

> [!NOTE]
> - Visual Studio Marketplace zawiera rozszerzenia VSIX i MSI. Okno dialogowe Rozszerzenia i aktualizacje nie można włączyć ani wyłączyć rozszerzeń opartych na ucho.
> - Jeśli rozszerzenie oparte na msi zawiera plik *extension.vsixmanifest,* rozszerzenie pojawi się w oknie dialogowym **Rozszerzenia i aktualizacje.**

::: moniker-end

::: moniker range=">=vs-2019"

Rozszerzenia można instalować z [programu Visual Studio Marketplace](https://marketplace.visualstudio.com) lub okna dialogowego Zarządzanie rozszerzeniami w programie Visual Studio.

Aby zainstalować rozszerzenia z poziomu programu Visual Studio:

1. W **rozszerzeń** > **Zarządzaj rozszerzeniami**znajdź rozszerzenie, które chcesz zainstalować. (Jeśli znasz nazwę lub część nazwy rozszerzenia, możesz wyszukać w oknie **wyszukiwania).**

2. Wybierz przycisk **Download** (Pobierz).

   Rozszerzenie jest zaplanowane do zainstalowania. Twoje rozszerzenie zostanie zainstalowane po zamknięciu wszystkich wystąpień programu Visual Studio.

Podczas próby instalacji rozszerzenia, które ma zależności, instalator sprawdza, czy są one już zainstalowane. Jeśli nie są zainstalowane, okno dialogowe **Zarządzanie rozszerzeniami** zawiera listę zależności, które muszą zostać zainstalowane przed zainstalowaniem rozszerzenia.

### <a name="install-without-using-the-manage-extensions-dialog-box"></a>Instalowanie bez korzystania z okna dialogowego Zarządzanie rozszerzeniami

Rozszerzenia, które zostały spakowane w plikach *vsix* mogą być dostępne w lokalizacjach innych niż Visual Studio Marketplace. Okno **dialogowe** > Zarządzanie rozszerzeniami nie może**wykryć** tych plików, ale można zainstalować plik *vsix,* klikając dwukrotnie plik lub wybierając plik i naciskając klawisz **Enter**. Następnie postępuj zgodnie z instrukcjami. Po zainstalowaniu rozszerzenia można użyć okna dialogowego **Zarządzanie rozszerzeniami,** aby je włączyć, wyłączyć lub odinstalować.

> [!NOTE]
> - Visual Studio Marketplace zawiera rozszerzenia VSIX i MSI. Okno dialogowe Zarządzanie rozszerzeniami nie może włączać ani wyłączać rozszerzeń opartych na uchybiłszych.
> - Jeśli rozszerzenie oparte na msi zawiera plik *extension.vsixmanifest,* rozszerzenie pojawi się w oknie dialogowym **Zarządzanie rozszerzeniami.**

::: moniker-end

## <a name="uninstall-or-disable-an-extension"></a>Odinstalowywanie lub wyłączanie rozszerzenia

Jeśli nie chcesz już dłużej używać rozszerzenia, możesz je wyłączyć lub odinstalować. Wyłączone rozszerzenie jest wciąż zainstalowane, ale nie jest załadowane. Znajdź rozszerzenie i kliknij przycisk **Odinstaluj** lub **Wyłącz**. Uruchom ponownie program Visual Studio, aby zwolnić wyłączone rozszerzenie.

> [!NOTE]
> Można wyłączyć rozszerzenia VSIX, ale nie rozszerzenia, które zostały zainstalowane przy użyciu msi. Rozszerzenia zainstalowane msi można tylko odinstalować.

## <a name="per-user-and-administrative-extensions"></a>Rozszerzenia na użytkownika i administracyjne

Większość rozszerzeń jest dla użytkownika i jest instalowana w folderze *%LocalAppData%\Microsoft\VisualStudio\\<wersji\>programu Visual Studio \Rozszerzenia.\\ * Kilka rozszerzeń to rozszerzenia administracyjne i są instalowane w * \<folderze instalacyjnym programu Visual Studio>\Common7\IDE\Extensions\\ * folderu.

Aby chronić system przed rozszerzeniami, które mogą zawierać błędy lub złośliwy kod, można ograniczyć rozszerzenia na użytkownika, aby załadować tylko wtedy, gdy program Visual Studio jest uruchamiany z normalnymi uprawnieniami użytkownika. Oznacza to, że rozszerzenia na użytkownika są wyłączone, gdy program Visual Studio jest uruchamiany z podwyższonym poziomem uprawnień.

Aby ograniczyć obciążenie rozszerzeń na użytkownika:

1. Otwórz stronę opcji rozszerzeń **(Opcje narzędzi** > **Options** > **rozszerzenia****środowiska).** > 

2. Wyczyść pole wyboru **Wczytanie rozszerzenia obciążenia na użytkownika podczas uruchamiania jako administrator.**

3. Uruchom ponownie program Visual Studio.

## <a name="automatic-extension-updates"></a>Automatyczne aktualizacje rozszerzeń

Rozszerzenia są aktualizowane automatycznie, gdy nowa wersja jest dostępna w programie Visual Studio Marketplace. Nowa wersja rozszerzenia jest wykrywana i instalowana w tle. Przy następnym otwarciu programu Visual Studio zostanie uruchomiona nowa wersja rozszerzenia.

Jeśli chcesz wyłączyć aktualizacje automatyczne, możesz wyłączyć tę funkcję dla wszystkich rozszerzeń lub tylko dla określonych rozszerzeń.

::: moniker range="vs-2017"

- Aby wyłączyć aktualizacje automatyczne dla wszystkich rozszerzeń, wybierz łącze **Zmień ustawienia rozszerzeń i aktualizacji** w oknie dialogowym Rozszerzenia i**aktualizacje** **narzędzi.** >  W oknie dialogowym **Opcje** wyeznańczyć pozycję **Automatycznie aktualizuj rozszerzenia**.

- Aby wyłączyć aktualizacje automatyczne dla określonego rozszerzenia, wyeznańcz opcję **Automatycznie aktualizuj to rozszerzenie** w okienku szczegółów rozszerzenia po prawej stronie okna dialogowego Rozszerzenia i **aktualizacje.**

::: moniker-end

::: moniker range=">=vs-2019"

- Aby wyłączyć aktualizacje automatyczne dla wszystkich rozszerzeń, wybierz łącze **Zmienianie ustawień rozszerzeń** w oknie dialogowym **Zarządzanie rozszerzeniami.** > **Manage Extensions** W oknie dialogowym **Opcje** wyeznańczyć pozycję **Automatycznie aktualizuj rozszerzenia**.

- Aby wyłączyć aktualizacje automatyczne dla określonego rozszerzenia, wyeznańcz opcję **Automatycznie aktualizuj to rozszerzenie** w okienku szczegółów rozszerzenia po prawej stronie okna dialogowego Zarządzanie **rozszerzeniami.**

::: moniker-end

## <a name="crash-and-unresponsiveness-notifications"></a>Powiadomienia o awariach i braku reakcji

Visual Studio powiadamia, jeśli podejrzewa, że rozszerzenie było zaangażowane w awarii podczas poprzedniej sesji. Gdy program Visual Studio ulegnie awarii, przechowuje stos wyjątków. Następnym uruchomieniu programu Visual Studio sprawdza stos, począwszy od liścia i pracy w kierunku bazy. Jeśli program Visual Studio stwierdzi, że ramka należy do modułu, który jest częścią zainstalowanego i włączonego rozszerzenia, pokazuje powiadomienie.

Visual Studio powiadamia również, jeśli podejrzewa, że rozszerzenie powoduje, że interfejs użytkownika nie odpowiada.

Gdy te powiadomienia są wyświetlane, możesz zignorować powiadomienie lub podjąć jedną z następujących czynności:

::: moniker range="vs-2017"

- Wybierz **pozycję Wyłącz to rozszerzenie**. Visual Studio wyłącza rozszerzenie i informuje, czy należy ponownie uruchomić system, aby wyłączenie zostało zastosowane. Rozszerzenie można ponownie włączyć w oknie dialogowym**Rozszerzenia i aktualizacje** **narzędzi,** > jeśli chcesz.

::: moniker-end

::: moniker range=">=vs-2019"

- Wybierz **pozycję Wyłącz to rozszerzenie**. Visual Studio wyłącza rozszerzenie i informuje, czy należy ponownie uruchomić system, aby wyłączenie zostało zastosowane. Rozszerzenie można ponownie włączyć w oknie dialogowym **Zarządzanie rozszerzeniami,** > **Manage Extensions** jeśli chcesz.

::: moniker-end

- Wybierz pozycję **Nigdy więcej nie pokazuj tego komunikatu**.

  - Jeśli powiadomienie dotyczy awarii w poprzedniej sesji, Visual Studio nie wyświetla już powiadomienia o awarii skojarzonej z tym rozszerzeniem. Visual Studio będzie nadal wyświetlać powiadomienia, gdy brak odpowiedzi może być skojarzony z tym rozszerzeniem lub w przypadku awarii lub braku odpowiedzi, które mogą być skojarzone z innymi rozszerzeniami.
  - Jeśli powiadomienie dotyczy braku odpowiedzi, zintegrowane środowisko programistyczne (IDE) nie jest już wyświetlane powiadomienie, gdy to rozszerzenie jest skojarzone z braku odpowiedzi. Visual Studio nadal będzie wyświetlać powiadomienia związane z awariami dla tego rozszerzenia i powiadomień związanych z awariami i nieodpowiadalnością dla innych rozszerzeń.

- Wybierz pozycję **Dowiedz się więcej,** aby przejść do tej strony.

- Wybierz przycisk **X** na końcu powiadomienia, aby odrzucić powiadomienie. Pojawi się nowe powiadomienie dla przyszłych wystąpień rozszerzenia skojarzonego z awarią lub nieodpowiadaniem interfejsu użytkownika.

> [!NOTE]
> Nie odpowiadanie interfejsu użytkownika lub powiadomienie o awarii oznacza tylko, że jeden z modułów rozszerzenia był na stosie, gdy interfejs użytkownika nie odpowiadał lub gdy wystąpiła awaria. Nie musi to oznaczać, że samo rozszerzenie było winowajcą. Jest możliwe, że rozszerzenie o nazwie kod, który jest częścią programu Visual Studio, co z kolei spowodowało brak odpowiedzi interfejsu użytkownika lub awarii. Jednak powiadomienie może być nadal przydatne, jeśli rozszerzenie, które doprowadziło do braku odpowiedzi interfejsu użytkownika lub awarii nie jest dla Ciebie ważne. W takim przypadku wyłączenie rozszerzenia pozwala uniknąć braku reakcji interfejsu użytkownika lub awarii w przyszłości, bez wpływu na produktywność.

## <a name="samples"></a>Samples

Po zainstalowaniu przykładu online, rozwiązanie jest przechowywane w dwóch miejscach:

- Kopia robocza jest przechowywana w lokalizacji określonej podczas tworzenia projektu.

- Oddzielna kopia główna jest przechowywana na komputerze.

::: moniker range="vs-2017"

Za pomocą okna dialogowego **Rozszerzenia i aktualizacje** **narzędzi** > można wykonywać następujące przykłady:

::: moniker-end

::: moniker range=">=vs-2019"

Za pomocą okna dialogowego **Zarządzanie** > **rozszerzeniami** można wykonywać następujące przykładowe zadania:

::: moniker-end

- Wypisanie listy kopii głównych przykładów, które zostały zainstalowane.

- Wyłączenie lub odinstalowanie kopii głównej przykładu.

- Zainstalowanie pakietów przykładów, które są zbiorami przykładów odnoszących się do technologii lub funkcji.

- Instalowanie pojedynczych przykładów online.

- Wyświetlanie powiadomień o aktualizacjach, gdy zostaną opublikowane zmiany kodu źródłowego dla zainstalowanych przykładów.

- Zaktualizuj główną kopię zainstalowanego przykładu, gdy jest powiadomienie o aktualizacji.

## <a name="see-also"></a>Zobacz też

- [Witryna Visual Studio Marketplace](https://marketplace.visualstudio.com)
- [Visual Studio SDK](../extensibility/visual-studio-sdk.md)
