---
title: Poprawianie wydajności dodatku VSTO
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
ms.openlocfilehash: 79f1c4a55321a1b039cc2702b1040e2ab9d4ac9d
ms.sourcegitcommit: e98db44f3a33529b0ba188d24390efd09e548191
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2019
ms.locfileid: "71255642"
---
# <a name="improve-the-performance-of-a-vsto-add-in"></a>Poprawianie wydajności dodatku VSTO
  Możesz dać użytkownikom lepszy komfort, optymalizując dodatki narzędzi VSTO tworzone dla aplikacji pakietu Office, aby szybko uruchamiać, zamykać, otwierać elementy i wykonywać inne zadania. Jeśli dodatek VSTO jest przeznaczony dla programu Outlook, można również zmniejszyć prawdopodobieństwo wyłączenia dodatku VSTO z powodu niskiej wydajności. Możesz zwiększyć wydajność dodatku VSTO, implementując następujące strategie:

- [Załaduj Dodatki VSTO na żądanie](#Load).

- [Publikowanie rozwiązań pakietu Office przy użyciu Instalator Windows](#Publish).

- [Obejście odbicia wstążki](#Bypass).

- [Wykonywanie kosztownych operacji w osobnym wątku wykonania](#Perform).

  Aby uzyskać więcej informacji na temat optymalizowania dodatku VSTO dla programu Outlook, zobacz [kryteria wydajności, które umożliwiają włączenie dodatków VSTO](http://go.microsoft.com/fwlink/?LinkID=266503).

## <a name="Load"></a>Załaduj Dodatki VSTO na żądanie
 Dodatek VSTO można skonfigurować do załadowania tylko w następujących okolicznościach:

- Pierwszy raz, gdy użytkownik uruchamia aplikację po zainstalowaniu dodatku VSTO.

- Gdy użytkownik po raz pierwszy współdziała z dodatkiem VSTO po uruchomieniu aplikacji w dowolnym momencie.

  Na przykład dodatek VSTO może wypełnić arkusz danymi, gdy użytkownik wybierze przycisk niestandardowy z etykietą **Pobierz moje dane**. Aplikacja musi załadować dodatek Narzędzia VSTO co najmniej jeden raz, aby na Wstążce pojawił się przycisk **Pobierz moje dane** . Jednak dodatek VSTO nie ładuje się ponownie, gdy użytkownik uruchomi aplikację przy następnym uruchomieniu. Dodatek VSTO ładuje się tylko wtedy, gdy użytkownik wybierze przycisk **Pobierz moje dane** .

### <a name="to-configure-a-clickonce-solution-to-load-vsto-add-ins-on-demand"></a>Aby skonfigurować rozwiązanie ClickOnce do ładowania dodatków VSTO na żądanie

1. W **Eksplorator rozwiązań**wybierz węzeł projektu.

2. Na pasku menu wybierz **widoku** > **stron właściwości**.

3. Na karcie **Publikowanie** wybierz przycisk **Opcje** .

4. W oknie dialogowym **Opcje publikowania** wybierz pozycję **Ustawienia pakietu Office** , wybierz opcję **Załaduj na żądanie** , a następnie wybierz przycisk **OK** .

### <a name="to-configure-a-windows-installer-solution-to-load-vsto-add-ins-on-demand"></a>Aby skonfigurować Instalator Windows rozwiązanie do ładowania dodatków VSTO na żądanie

1. W rejestrze `LoadBehavior` Ustaw klucz **_identyfikatora dodatku_ _głównego_\\\Software\Microsoft\Office_ApplicationName_\Addins\\** na **0x10**.

     Aby uzyskać więcej informacji, zobacz [wpisy rejestru dotyczące dodatków narzędzi VSTO](../vsto/registry-entries-for-vsto-add-ins.md).

### <a name="to-configure-a-solution-to-load-vsto-add-ins-on-demand-while-you-debug-the-solution"></a>Aby skonfigurować rozwiązanie do ładowania dodatków VSTO na żądanie podczas debugowania rozwiązania

1. `LoadBehavior` Utwórz skrypt ustawiający wpis  **_głównego_klucza\\_identyfikatora dodatku_ \Software\Microsoft\Office_ApplicationName_\Addins\\** na **0x10**.

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

     Aby uzyskać informacje na temat sposobu tworzenia zdarzenia po kompilacji w C# projekcie, zobacz [How to: Określ &#40;zdarzenia kompilacji C&#35;&#41;](../ide/how-to-specify-build-events-csharp.md).

     Aby uzyskać informacje na temat sposobu tworzenia zdarzenia po kompilacji w projekcie Visual Basic, zobacz [How to: Określ &#40;&#41;VisualBasic](../ide/how-to-specify-build-events-visual-basic.md)zdarzeń kompilacji.

## <a name="Publish"></a>Publikowanie rozwiązań pakietu Office przy użyciu Instalator Windows
 W przypadku publikowania rozwiązania przy użyciu Instalator Windows narzędzia programu Visual Studio 2010 Tools for Office Runtime pomijają następujące kroki podczas ładowania dodatku VSTO.

- Sprawdzanie poprawności schematu manifestu.

- Automatyczne sprawdzanie dostępności aktualizacji.

- Weryfikowanie podpisów cyfrowych manifestów wdrożenia.

  > [!NOTE]
  > Takie podejście nie jest konieczne, jeśli dodatek VSTO zostanie wdrożony w bezpiecznej lokalizacji na komputerach użytkowników.

  Aby uzyskać więcej informacji, zobacz [wdrażanie rozwiązania biurowego przy użyciu Instalator Windows](../vsto/deploying-an-office-solution-by-using-windows-installer.md).

## <a name="Bypass"></a>Obejście odbicia wstążki
 W przypadku tworzenia rozwiązania przy użyciu [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)]programu upewnij się, że użytkownicy zainstalowali najnowszą wersję środowiska uruchomieniowego Visual Studio 2010 Tools for Office podczas wdrażania rozwiązania. Starsze wersje środowiska uruchomieniowego programu VSTO odzwierciedlone w zestawach rozwiązań w celu zlokalizowania dostosowań Wstążki. Ten proces może spowodować spowolnienie ładowania dodatku VSTO.

 Alternatywnie można zapobiec używaniu odbicia dla wszystkich wersji narzędzi Visual Studio 2010 Tools for Office Runtime do identyfikowania dostosowań Wstążki. Aby postępować zgodnie z tą strategią, Zastąp `CreateRibbonExtensibility` metodę i jawnie Zwróć obiekty wstążki. Jeśli dodatek VSTO nie zawiera żadnych dostosowań wstążki, Wróć `null` wewnątrz metody.

 Poniższy przykład zwraca obiekt wstążki na podstawie wartości pola.

 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_ribbon_choose_ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_ribbon_choose_ribbon_4/ThisWorkbook.cs#1)]

## <a name="Perform"></a>Wykonywanie kosztownych operacji w osobnym wątku wykonywania
 Należy rozważyć wykonywanie zadań czasochłonnych (takich jak długotrwałe zadania, połączenia z bazami danych lub inne rodzaje wywołań sieciowych) w osobnym wątku. Aby uzyskać więcej informacji, zobacz [Obsługa wątkowości w pakiecie Office](../vsto/threading-support-in-office.md).

> [!NOTE]
> Cały kod, który wywołuje do modelu obiektów pakietu Office, musi być wykonywany w wątku głównym.

## <a name="see-also"></a>Zobacz także

- [Żądanie — ładowanie dodatków narzędzi VSTO](https://blogs.msdn.microsoft.com/andreww/2008/07/14/demand-loading-vsto-add-ins/)
- [Opóźnienie ładowania środowiska CLR w dodatkach pakietu Office](https://blogs.msdn.microsoft.com/andreww/2008/04/19/delay-loading-the-clr-in-office-add-ins/)
- [Tworzenie dodatków narzędzi VSTO dla pakietu Office przy użyciu programu Visual Studio](create-vsto-add-ins-for-office-by-using-visual-studio.md)
