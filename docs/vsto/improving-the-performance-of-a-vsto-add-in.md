---
title: Poprawa wydajności dodatku VSTO
ms.date: 02/02/2017
ms.topic: conceptual
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: dccff7206aa9ef71596816d34a863695a10aff6b
ms.sourcegitcommit: b32fbbcbc43910b0ed7ce79aa9a22f2ed36ab57e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2020
ms.locfileid: "79416552"
---
# <a name="improve-the-performance-of-a-vsto-add-in"></a>Poprawa wydajności dodatku VSTO
  Możesz zapewnić użytkownikom lepsze środowisko, optymalizując dodatki VSTO utworzone dla aplikacji pakietu Office, aby szybko uruchamiały się, zamykały, otwierały elementy i wykonywały inne zadania. Jeśli dodatek VSTO jest dla programu Outlook, można również zmniejszyć prawdopodobieństwo, że dodatek VSTO zostanie wyłączony z powodu niskiej wydajności. Można zwiększyć wydajność dodatku VSTO, implementując następujące strategie:

- [Załaduj dodatki VSTO na żądanie](#Load).

- [Publikuj rozwiązania pakietu Office przy użyciu Instalatora Windows](#Publish).

- [Omiń odbicie Wstążki](#Bypass).

- [Wykonaj kosztowne operacje w oddzielnym wątku wykonywania](#Perform).

  Aby uzyskać więcej informacji na temat optymalizacji dodatku VSTO programu Outlook, zobacz [Kryteria wydajności, aby zachować włączone dodatki VSTO](/previous-versions/office/jj228679(v=office.15)#performance-criteria-for-keeping-add-ins-enabled).

## <a name="load-vsto-add-ins-on-demand"></a><a name="Load"></a>Ładowanie dodatków VSTO na żądanie
 Dodatek VSTO można skonfigurować w taki sposób, aby ładował się tylko w następujących okolicznościach:

- Po pierwszym uruchomieniu aplikacji po zainstalowaniu dodatku VSTO.

- Po raz pierwszy, że użytkownik wchodzi w interakcję z dodatkiem VSTO po uruchomieniu aplikacji w dowolnym następnym czasie.

  Na przykład dodatek VSTO może wypełnić arkusz danymi, gdy użytkownik wybierze przycisk niestandardowy oznaczony jako **Pobierz moje dane**. Aplikacja musi załadować dodatek VSTO co najmniej jeden raz, aby przycisk **Pobierz moje dane** mógł pojawić się na Wstążce. Jednak dodatek VSTO nie ładuje się ponownie, gdy użytkownik uruchamia aplikację następnym razem. Dodatek VSTO ładuje się tylko wtedy, gdy użytkownik wybierze przycisk **Pobierz moje dane.**

### <a name="to-configure-a-clickonce-solution-to-load-vsto-add-ins-on-demand"></a>Aby skonfigurować rozwiązanie ClickOnce do ładowania dodatków VSTO na żądanie

1. W **Eksploratorze rozwiązań**wybierz węzeł projektu.

2. Na pasku menu wybierz pozycję **Wyświetl** > **strony właściwości**.

3. Na karcie **Publikowanie** wybierz przycisk **Opcje.**

4. W oknie dialogowym **Opcje publikowania** wybierz pozycję pozycji listy Ustawienia **pakietu Office,** wybierz opcję **Załaduj na żądanie,** a następnie wybierz przycisk **OK.**

### <a name="to-configure-a-windows-installer-solution-to-load-vsto-add-ins-on-demand"></a>Aby skonfigurować rozwiązanie Instalatora Windows do ładowania dodatków VSTO na żądanie

1. W rejestrze ustaw `LoadBehavior` wpis ** _klucza_identyfikatora dodatku\\0x10 głównego \Software\Microsoft\Office_ApplicationName_\Addins\\** . **0x10**

     Aby uzyskać więcej informacji, zobacz [Wpisy rejestru dla dodatków VSTO](../vsto/registry-entries-for-vsto-add-ins.md).

### <a name="to-configure-a-solution-to-load-vsto-add-ins-on-demand-while-you-debug-the-solution"></a>Aby skonfigurować rozwiązanie do ładowania dodatków VSTO na żądanie podczas debugowania rozwiązania

1. Utwórz skrypt, `LoadBehavior` który ustawia wpis klucza identyfikatora dodatku **0x10** ** _dla katalogu głównego_\Software\Microsoft\Office\\_ApplicationName_\Addins\\** .

     Poniższy kod przedstawia przykład tego skryptu.

    ```cmd/sh
    [HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\MyAddIn]
    "Description"="MyAddIn"
    "FriendlyName"="MyAddIn"
    "LoadBehavior"=dword:00000010
    "Manifest"="c:\\Temp\\MyAddIn\\bin\\Debug\\MyAddIn.vsto|vstolocal"

    ```

2. Utwórz zdarzenie po kompilacji, które aktualizuje rejestr przy użyciu skryptu.

     Poniższy kod przedstawia przykład ciągu polecenia, który można dodać do zdarzenia po kompilacji.

    ```cmd/sh
    regedit /s "$(SolutionDir)$(SolutionName).reg"

    ```

     Aby uzyskać informacje dotyczące tworzenia zdarzenia po kompilacji w projekcie języka C#, zobacz [Jak: Określanie zdarzeń kompilacji &#40;C&#35;&#41;](../ide/how-to-specify-build-events-csharp.md).

     Aby uzyskać informacje dotyczące tworzenia zdarzenia po kompilacji w projekcie języka Visual Basic, zobacz [Jak: Określanie zdarzeń kompilacji &#40;języka Visual Basic&#41;](../ide/how-to-specify-build-events-visual-basic.md).

## <a name="publish-office-solutions-by-using-windows-installer"></a><a name="Publish"></a>Publikowanie rozwiązań pakietu Office przy użyciu Instalatora Windows
 Jeśli publikujesz rozwiązanie przy użyciu Instalatora Windows, środowisko wykonawcze Visual Studio 2010 Tools for Office pomija następujące kroki podczas ładowania dodatku VSTO.

- Sprawdzanie poprawności schematu manifestu.

- Automatyczne sprawdzanie dostępności aktualizacji.

- Sprawdzanie poprawności podpisów cyfrowych manifestów wdrażania.

  > [!NOTE]
  > Takie podejście nie jest konieczne, jeśli wdrożysz dodatek VSTO w bezpiecznej lokalizacji na komputerach użytkowników.

  Aby uzyskać więcej informacji, zobacz [Wdrażanie rozwiązania pakietu Office przy użyciu Instalatora Windows](../vsto/deploying-a-vsto-solution-by-using-windows-installer.md).

## <a name="bypass-ribbon-reflection"></a><a name="Bypass"></a>Odbicie bypass ribbon
 Jeśli tworzysz rozwiązanie [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)]przy użyciu , upewnij się, że użytkownicy zainstalowali najnowszą wersję środowiska wykonawczego Visual Studio 2010 tools for Office podczas wdrażania rozwiązania. Starsze wersje środowiska wykonawczego VSTO odzwierciedlone w zestawach rozwiązań w celu zlokalizowania dostosowań wstążki. Ten proces może spowodować, że dodatek VSTO będzie ładowany wolniej.

 Alternatywnie można uniemożliwić dowolnej wersji środowiska wykonawczego Visual Studio 2010 Tools for Office przy użyciu odbicia w celu zidentyfikowania dostosowań wstążki. Aby wykonać tę strategię, `CreateRibbonExtensibility` należy zastąpić metodę i jawnie zwrócić obiekty Wstążki. Jeśli dodatek VSTO nie zawiera żadnych dostosowań `null` wstążki, wróć do metody.

 Poniższy przykład zwraca obiekt Wstążki na podstawie wartości pola.

 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_ribbon_choose_ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_ribbon_choose_ribbon_4/ThisWorkbook.cs#1)]

## <a name="perform-expensive-operations-in-a-separate-execution-thread"></a><a name="Perform"></a>Wykonywanie kosztownych operacji w oddzielnym wątku wykonania
 Rozważ wykonywanie czasochłonnych zadań (takich jak długotrwałe zadania, połączenia z bazą danych lub inne rodzaje wywołań sieciowych) w oddzielnym wątku. Aby uzyskać więcej informacji, zobacz [Obsługa wątków w pakiecie Office](../vsto/threading-support-in-office.md).

> [!NOTE]
> Cały kod, który wywołuje model obiektu pakietu Office musi wykonać w wątku głównym.

## <a name="see-also"></a>Zobacz też

- [Wczytywanie zapotrzebowania dodatki VSTO](https://blogs.msdn.microsoft.com/andreww/2008/07/14/demand-loading-vsto-add-ins/)
- [Opóźnianie ładowania urządzenia CLR w dodatkach pakietu Office](https://blogs.msdn.microsoft.com/andreww/2008/04/19/delay-loading-the-clr-in-office-add-ins/)
- [Tworzenie dodatków narzędzi VSTO dla pakietu Office w programie Visual Studio](create-vsto-add-ins-for-office-by-using-visual-studio.md)
