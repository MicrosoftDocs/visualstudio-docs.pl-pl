---
title: Poprawianie wydajności dodatku VSTO
description: Dowiedz się, jak zoptymalizować dodatki VSTO, które tworzysz dla aplikacji pakietu Office, aby szybko uruchamiały się, zamykały, otwierały elementy i wykonywać inne zadania.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: 29035f4867421ed3f05e5f0c3a5c196f58b7ab34
ms.sourcegitcommit: 4b40aac584991cc2eb2186c3e4f4a7fcd522f607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2021
ms.locfileid: "107825124"
---
# <a name="improve-the-performance-of-a-vsto-add-in"></a>Poprawianie wydajności dodatku VSTO
  Możesz zapewnić użytkownikom lepsze środowisko, optymalizując dodatki VSTO, które tworzysz dla aplikacji pakietu Office, aby szybko uruchamiać, zamykać, otwierać elementy i wykonywać inne zadania. Jeśli dodatek VSTO jest dla programu Outlook, możesz również zmniejszyć prawdopodobieństwo wyłączenia dodatku VSTO z powodu niskiej wydajności. Wydajność dodatku VSTO można zwiększyć, implementując następujące strategie:

- [Załaduj dodatki VSTO na żądanie.](#Load)

- [Publikowanie rozwiązań pakietu Office przy użyciu Instalator Windows](#Publish).

- [Pomiń odbicie wstążki](#Bypass).

- [Wykonywanie kosztownych operacji w osobnym wątku wykonywania](#Perform).

  Aby uzyskać więcej informacji na temat sposobu optymalizacji dodatku VSTO programu Outlook, zobacz [Performance criteria to keep VSTO Add-ins enabled](/previous-versions/office/jj228679(v=office.15)#performance-criteria-for-keeping-add-ins-enabled)(Kryteria wydajności w celu utrzymania włączonych dodatków VSTO).

## <a name="load-vsto-add-ins-on-demand"></a><a name="Load"></a> Ładowanie dodatków VSTO na żądanie
 Dodatek VSTO można skonfigurować do ładowania tylko w następujących okolicznościach:

- Przy pierwszym uruchamianiu aplikacji przez użytkownika po zainstalowaniu dodatku VSTO.

- Za pierwszym razem, gdy użytkownik wchodzi w interakcję z dodatku VSTO po uruchomieniu aplikacji w dowolnym późniejszym czasie.

  Na przykład dodatek VSTO może wypełnić arkusz danymi, gdy użytkownik wybierze niestandardowy przycisk z etykietą **Pobierz moje dane.** Aplikacja musi załadować dodatek VSTO co najmniej raz, aby przycisk Pobierz moje dane pojawił się na wstążce.  Jednak dodatek VSTO nie zostanie załadowany ponownie, gdy użytkownik następnym razem uruchomi aplikację. Dodatek VSTO jest ładowany tylko wtedy, gdy użytkownik wybierze przycisk **Pobierz moje** dane.

### <a name="to-configure-a-clickonce-solution-to-load-vsto-add-ins-on-demand"></a>Aby skonfigurować rozwiązanie ClickOnce do ładowania dodatków VSTO na żądanie

1. W **Eksplorator rozwiązań** wybierz węzeł projektu.

2. Na pasku menu wybierz pozycję **Wyświetl**  >  **strony właściwości.**

3. Na karcie **Publikowanie** wybierz **przycisk** Opcje.

4. W **oknie dialogowym** Opcje publikowania wybierz element  listy Ustawienia pakietu **Office,** wybierz opcję Załaduj na żądanie, a następnie wybierz **przycisk OK.**

### <a name="to-configure-a-windows-installer-solution-to-load-vsto-add-ins-on-demand"></a>Aby skonfigurować Instalator Windows do ładowania dodatków VSTO na żądanie

1. W rejestrze ustaw wpis Główny `LoadBehavior` **\Software\Microsoft\Office \\ _ApplicationName_\Addins \\ _Klucz_** identyfikatora dodatku na **wartość 0x10**.

     Aby uzyskać więcej informacji, zobacz [Wpisy rejestru dla dodatków VSTO.](../vsto/registry-entries-for-vsto-add-ins.md)

### <a name="to-configure-a-solution-to-load-vsto-add-ins-on-demand-while-you-debug-the-solution"></a>Aby skonfigurować rozwiązanie do ładowania dodatków VSTO na żądanie podczas debugowania rozwiązania

1. Utwórz skrypt, który ustawia wpis główny `LoadBehavior` **\Software\Microsoft\Office \\ _ApplicationName_\Addins \\ _Klucz_** identyfikatora dodatku na **0x10**.

     Poniższy kod przedstawia przykład tego skryptu.

    ```cmd/sh
    [HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\MyAddIn]
    "Description"="MyAddIn"
    "FriendlyName"="MyAddIn"
    "LoadBehavior"=dword:00000010
    "Manifest"="c:\\Temp\\MyAddIn\\bin\\Debug\\MyAddIn.vsto|vstolocal"

    ```

2. Utwórz zdarzenie po kompilacji, które aktualizuje rejestr przy użyciu skryptu .

     Poniższy kod przedstawia przykład ciągu polecenia, który można dodać do zdarzenia po kompilacji.

    ```cmd/sh
    regedit /s "$(SolutionDir)$(SolutionName).reg"

    ```

     Aby uzyskać informacje na temat sposobu tworzenia zdarzenia po kompilacji w projekcie języka C#, zobacz How [to: Specify build events &#40;C&#35;&#41;](../ide/how-to-specify-build-events-csharp.md).

     Aby uzyskać informacje na temat tworzenia zdarzenia po kompilacji w projekcie Visual Basic, zobacz Jak określić zdarzenia kompilacji [w &#40;Visual Basic&#41;](../ide/how-to-specify-build-events-visual-basic.md).

## <a name="publish-office-solutions-by-using-windows-installer"></a><a name="Publish"></a> Publikowanie rozwiązań pakietu Office przy użyciu Instalator Windows
 Jeśli publikujesz rozwiązanie przy użyciu programu Instalator Windows, środowisko uruchomieniowe narzędzi programu Visual Studio 2010 Tools for Office pomija następujące kroki podczas ładowania dodatku narzędzi VSTO.

- Sprawdzania poprawności schematu manifestu.

- Automatyczne sprawdzanie aktualizacji.

- Weryfikację podpisów cyfrowych manifestów wdrożenia.

  > [!NOTE]
  > Takie podejście nie jest konieczne w przypadku wdrażania dodatku VSTO w bezpiecznej lokalizacji na komputerach użytkowników.

  Aby uzyskać więcej informacji, zobacz [Wdrażanie rozwiązania pakietu Office przy użyciu Instalator Windows](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

## <a name="bypass-ribbon-reflection"></a><a name="Bypass"></a> Pomijanie odbicia wstążki
 Jeśli tworzysz rozwiązanie przy użyciu programu , upewnij się, że użytkownicy mają zainstalowaną najnowszą wersję środowiska uruchomieniowego [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)] narzędzi Visual Studio 2010 Tools for Office podczas wdrażania rozwiązania. Starsze wersje środowiska uruchomieniowego VSTO są odzwierciedlane w zestawach rozwiązań w celu zlokalizowania dostosowań wstążki. Ten proces może spowodować, że dodatek VSTO będzie ładować się wolniej.

 Alternatywnie można uniemożliwić dowolnej wersji środowiska uruchomieniowego narzędzia Visual Studio 2010 dla pakietu Office używanie odbicia w celu identyfikowania dostosowań wstążki. Aby stosować tę strategię, zastąp `CreateRibbonExtensibility` metodę i jawnie zwróć obiekty wstążki. Jeśli dodatek VSTO nie zawiera żadnych dostosowań wstążki, wróć `null` do metody .

 Poniższy przykład zwraca obiekt wstążki na podstawie wartości pola.

 :::code language="vb" source="../vsto/codesnippet/VisualBasic/trin_ribbon_choose_ribbon_4/ThisWorkbook.vb" id="Snippet1":::
 :::code language="csharp" source="../vsto/codesnippet/CSharp/trin_ribbon_choose_ribbon_4/ThisWorkbook.cs" id="Snippet1":::

## <a name="perform-expensive-operations-in-a-separate-execution-thread"></a><a name="Perform"></a> Wykonywanie kosztownych operacji w osobnym wątku wykonywania
 Rozważ wykonywanie czasochłonnych zadań (takich jak długotrwałe zadania, połączenia bazy danych lub inne rodzaje wywołań sieciowych) w osobnym wątku. Aby uzyskać więcej informacji, zobacz [Obsługa wątków w psłudze Office.](../vsto/threading-support-in-office.md)

> [!NOTE]
> Cały kod, który wywołuje model obiektów pakietu Office, musi być wykonywany w wątku głównym.

## <a name="see-also"></a>Zobacz też

- [Ładowanie na żądanie dodatków VSTO](/archive/blogs/andreww/demand-loading-vsto-add-ins)
- [Opóźnienie ładowania clr w dodatki pakietu Office](/archive/blogs/andreww/delay-loading-the-clr-in-office-add-ins)
- [Tworzenie dodatków narzędzi VSTO dla pakietu Office w programie Visual Studio](create-vsto-add-ins-for-office-by-using-visual-studio.md)