---
title: Zwiększa wydajność dodatku narzędzi VSTO
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
ms.openlocfilehash: 2add0dfced6a3b8e8263dafe133ee3a2f86637f5
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63420937"
---
# <a name="improve-the-performance-of-a-vsto-add-in"></a>Poprawianie wydajności dodatku VSTO
  Można zapewnić użytkownikom lepsze środowisko, optymalizując dodatków narzędzi VSTO, które tworzysz dla aplikacji, aby szybko rozpocząć, zamknij usługi Office, Otwórz elementy i wykonywać inne zadania. W przypadku dodatku narzędzi VSTO dla programu Outlook, można także zmniejszyć ryzyko, że dodatku narzędzi VSTO dla programów będzie wyłączona z powodu niskiej wydajności. Aby zwiększyć wydajność dodatku narzędzi VSTO dla programów, należy wykonania następujących strategii:

- [Ładowanie dodatków narzędzi VSTO dla programów na żądanie](#Load).

- [Publikowanie rozwiązań pakietu Office przy użyciu Instalatora Windows](#Publish).

- [Pomiń odbicia wstążki](#Bypass).

- [Wykonywania kosztownych operacji w wątku wykonywania oddzielnych](#Perform).

  Aby uzyskać więcej informacji na temat optymalizowania dodatku narzędzi VSTO dla programu Outlook, zobacz [kryteria wydajności, aby zachować dodatków narzędzi VSTO włączone](http://go.microsoft.com/fwlink/?LinkID=266503).

## <a name="Load"></a> Ładowanie dodatków narzędzi VSTO dla programów na żądanie
 Można skonfigurować dodatku narzędzi VSTO załadować tylko w następujących okolicznościach:

- Po raz pierwszy po zainstalowaniu dodatku narzędzi VSTO dla programów jest, użytkownik uruchamia aplikację.

- Po raz pierwszy użytkownik wchodzi w interakcję z dodatku narzędzi VSTO po uruchomieniu aplikacji w dowolnym momencie kolejne.

  Na przykład dodatku narzędzi VSTO dla programów może wypełnić arkusza z danymi, gdy użytkownik wybierze przycisk niestandardowej, która jest oznaczona etykietą **Pobierz Moje dane**. Aplikacja musi załadować dodatku narzędzi VSTO dla programów co najmniej jeden raz, aby **Pobierz Moje dane** przycisk może znajdować się na Wstążce. Jednak dodatku narzędzi VSTO dla programów nie jest ładowana, ponownie po użytkownik uruchamia aplikację po następnym. Dodatek narzędzi VSTO dla programów ładuje tylko wtedy, gdy użytkownik wybierze **Pobierz Moje dane** przycisku.

### <a name="to-configure-a-clickonce-solution-to-load-vsto-add-ins-on-demand"></a>Aby skonfigurować rozwiązanie ClickOnce, aby załadować dodatków narzędzi VSTO dla programów na żądanie

1. W **Eksploratora rozwiązań**, wybierz węzeł projektu.

2. Na pasku menu wybierz **widoku** > **stron właściwości**.

3. Na **Publikuj** kartę, wybrać **opcje** przycisku.

4. W **opcji publikowania** okna dialogowego wybierz **ustawienia pakietu Office** elementu listy, wybierz polecenie **obciążenia na żądanie** opcji, a następnie wybierz **OK**przycisku.

### <a name="to-configure-a-windows-installer-solution-to-load-vsto-add-ins-on-demand"></a>Aby skonfigurować rozwiązanie Instalatora Windows, aby załadować dodatków narzędzi VSTO dla programów na żądanie

1. W rejestrze, ustaw `LoadBehavior` wpisu **_głównego_\Software\Microsoft\Office\\_ApplicationName_\Addins\\  _Identyfikator dodatku_** klucza **0x10**.

     Aby uzyskać więcej informacji, zobacz [wpisy rejestru dotyczące dodatków narzędzi VSTO](../vsto/registry-entries-for-vsto-add-ins.md).

### <a name="to-configure-a-solution-to-load-vsto-add-ins-on-demand-while-you-debug-the-solution"></a>Aby skonfigurować rozwiązanie, aby załadować dodatków narzędzi VSTO dla programów na żądanie, podczas debugowania rozwiązania

1. Utwórz skrypt, który ustawia `LoadBehavior` wpisu **_głównego_\Software\Microsoft\Office\\_ApplicationName_\Addins\\  _Identyfikator dodatku_** klucza **0x10**.

     Poniższy kod przedstawia przykład tego skryptu.

    ```cmd/sh
    [HKEY_CURRENT_USER\Software\Microsoft\Office\Excel\Addins\MyAddIn]
    "Description"="MyAddIn"
    "FriendlyName"="MyAddIn"
    "LoadBehavior"=dword:00000010
    "Manifest"="c:\\Temp\\MyAddIn\\bin\\Debug\\MyAddIn.vsto|vstolocal"

    ```

2. Utwórz zdarzenie po kompilacji, która aktualizuje rejestr przy użyciu skryptu.

     Poniższy kod przedstawia przykład ciąg polecenia, które można dodać do zdarzenia postkompilacyjnego.

    ```cmd/sh
    regedit /s "$(SolutionDir)$(SolutionName).reg"

    ```

     Aby uzyskać informacje o tym, jak utworzyć zdarzenia mające miejsce po kompilacji w C# projektu, zobacz [jak: Określanie zdarzeń kompilacji &#40;C&#35;&#41;](../ide/how-to-specify-build-events-csharp.md).

     Aby dowiedzieć się, jak utworzyć zdarzenie po kompilacji w projekcie w języku Visual Basic, zobacz [jak: Określanie zdarzeń kompilacji &#40;języka Visual Basic&#41;](../ide/how-to-specify-build-events-visual-basic.md).

## <a name="Publish"></a> Publikowanie rozwiązań pakietu Office przy użyciu Instalatora Windows
 Gdy będziesz publikować rozwiązanie usługi przy użyciu Instalatora Windows w Visual Studio 2010 Tools dla pakietu Office runtime dodatku narzędzi VSTO ładuje będzie pomija następujące kroki.

- Sprawdzanie poprawności schematu manifestu.

- Automatycznie sprawdzania dostępności aktualizacji.

- Weryfikowanie podpisów cyfrowych w manifesty wdrożenia.

  > [!NOTE]
  > To podejście nie jest konieczne, jeśli wdrożenie dodatku narzędzi VSTO dla programów do bezpiecznej lokalizacji na komputerach użytkowników.

  Aby uzyskać więcej informacji, zobacz [wdrażania rozwiązania pakietu Office przy użyciu Instalatora Windows](../vsto/deploying-an-office-solution-by-using-windows-installer.md).

## <a name="Bypass"></a> Obejście wstążki odbicia
 W przypadku tworzenia rozwiązania przy użyciu [!INCLUDE[vs_dev11_long](../sharepoint/includes/vs-dev11-long-md.md)], upewnij się, użytkownicy zainstalowano najnowszą wersję programu Visual Studio 2010 Tools dla pakietu Office runtime podczas wdrażania rozwiązania. Starsze wersje tego środowiska uruchomieniowego są uwzględniane w zestawy rozwiązań, aby zlokalizować dostosowań Wstążki. Ten proces może spowodować dodatku narzędzi VSTO dla programów do ładują się wolniej.

 Alternatywnie można zapobiec dowolnej wersji programu Visual Studio 2010 Tools dla pakietu Office runtime przy użyciu odbicia w celu zidentyfikowania dostosowań Wstążki. Aby skorzystać z tej strategii, należy zastąpić `CreateRibbonExtensibility` metody i jawnie zwracane obiekty wstążki. Jeśli dodatku narzędzi VSTO dla programów nie zawiera żadnych dostosowań Wstążki, zwracają `null` wewnątrz metody.

 Poniższy przykład zwraca obiekt wstążki, na podstawie wartości pola.

 [!code-vb[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/VisualBasic/trin_ribbon_choose_ribbon_4/ThisWorkbook.vb#1)]
 [!code-csharp[Trin_Ribbon_Choose_Ribbon#1](../vsto/codesnippet/CSharp/trin_ribbon_choose_ribbon_4/ThisWorkbook.cs#1)]

## <a name="Perform"></a> Wykonywania kosztownych operacji w wątku wykonywania oddzielnych
 Uwzględnić w harmonogramie czasochłonnych zadań (na przykład długotrwałe zadania, połączenia z bazą danych lub inne rodzaje wywołań sieci) w oddzielnym wątku. Aby uzyskać więcej informacji, zobacz [Obsługa wątkowości w Office](../vsto/threading-support-in-office.md).

> [!NOTE]
> Cały kod, który wywołuje w modelu obiektów programu pakietu Office muszą być wykonywane w wątku głównym.

## <a name="see-also"></a>Zobacz także

- [Żądanie załadowania narzędzi VSTO](https://blogs.msdn.microsoft.com/andreww/2008/07/14/demand-loading-vsto-add-ins/)
- [Opóźnienie ładowania CLR w dodatki pakietu Office](https://blogs.msdn.microsoft.com/andreww/2008/04/19/delay-loading-the-clr-in-office-add-ins/)
- [Tworzenie dodatków narzędzi VSTO dla pakietu Office przy użyciu programu Visual Studio](create-vsto-add-ins-for-office-by-using-visual-studio.md)
