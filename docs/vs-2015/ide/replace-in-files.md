---
title: Zastąp w plikach | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
f1_keywords:
- vs.findreplace.replaceinfiles
- vs.replaceinfiles
helpviewer_keywords:
- text searches, replacing text
- Find and Replace window, Replace in Files tab
- Replace in Files tab, Find and Replace window
ms.assetid: ca361466-53bd-44db-a28a-3a74bc03b028
caps.latest.revision: 33
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 87a9d344b6cad7d27979e73c73caf0dbf97f521d
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54779245"
---
# <a name="replace-in-files"></a>Zastąp w plikach
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Zastąp w plikach ** umożliwia wyszukiwanie kodu określonego zestawu plików dla ciągu lub wyrażenia i zmienić niektóre lub wszystkie znalezione dopasowania. Liczba znalezionych dopasowań i akcje wykonywane są wymienione w **Find Results** wybranego w oknie **wyniku opcje**.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz Importuj i Eksportuj ustawienia w menu Narzędzia. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska deweloperskiego, w programie Visual Studio](http://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
 Można użyć dowolnej z następujących metod, do wyświetlenia **Zamień w plikach** w **Znajdź i Zamień** okna.  
  
### <a name="to-display-replace-in-files"></a>Aby wyświetlić Zastąp w plikach  
  
1.  Na **Edytuj** menu, rozwiń węzeł **Znajdź i Zamień**.  
  
2.  Wybierz **Zamień w plikach**.  
  
     — lub —  
  
     Jeśli **Znajdź i Zamień** okno jest jeszcze otwarty, na pasku narzędzi, wybierz polecenie **Zamień w plikach**.  
  
## <a name="find-what"></a>Znajdź  
 Aby wyszukać nowy ciąg tekstowy lub wyrażenie, należy je określić w polu. Aby wyszukać dowolne z 20 ciągów, które wyszukiwane ostatnio, Otwórz listę, a następnie wybierz parametry, dla której chcesz wyszukać. Wybierz sąsiadujących **Konstruktor wyrażeń** przycisk, jeśli chcesz użyć co najmniej jednego wyrażenia regularne w wyszukiwanym ciągu. Aby uzyskać więcej informacji, zobacz [za pomocą wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
## <a name="replace-with"></a>Zamień  
 Aby zastąpić wystąpienia ciągu w **Znajdź** polu innym ciągiem, wprowadź ciąg zastępujący w **Zamień** pole. Można usunąć wystąpień w ciągu **Znajdź** polu, pozostaw to pole puste. Otwórz listę, aby wyświetlić 20 ciągów, dla których Przeszukano ostatnio. Wybierz sąsiadujących **Konstruktor wyrażeń** przycisk, jeśli chcesz używać jednego lub więcej wyrażeń regularnych w ciąg zastępujący. Aby uzyskać więcej informacji, zobacz [za pomocą wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
## <a name="look-in"></a>Szukaj w  
 Opcja wybrana z **Szukaj w** listy rozwijanej określa, czy **Zamień w plikach** przeszukuje tylko aktualnie aktywnych plików lub przeszukuje wszystkie pliki przechowywane w określonych folderach. Wybierz zakres wyszukiwania na liście, wpisz ścieżkę folderu lub kliknij **przeglądania (...)**  przycisk, aby wyświetlić **Choose Search Folders** okna dialogowego pole, a następnie wybierz zestaw folderów do wyszukiwania. Możesz również wpisać ścieżkę bezpośrednio do **przeszukania** pole.  
  
> [!NOTE]
>  Jeśli **przeszukania** wybrana opcja powoduje, że użytkownik może wyszukiwać pliku, który został wyewidencjonowany z kontrolą kodu źródłowego, przeszukiwany jest tylko wersja tego pliku, który został pobrany na komputer lokalny.  
  
## <a name="find-options"></a>Opcje znajdowania  
 Można rozwinąć lub zwinąć **opcje szukania** sekcji. Następujące opcje można zaznaczyć lub wyczyścić:  
  
 Uwzględnij wielkość liter  
 Po wybraniu **Find Results** systemu windows będą wyświetlane tylko wystąpień **Znajdź** ciąg, który są dopasowywane zarówno zawartość, jak i wielkością liter. Na przykład wyszukiwanie "MyObject" za pomocą **Uwzględnij wielkość liter** wybrane zostaną zwrotu "MyObject", ale nie "myobject" lub "MYOBJECT."  
  
 Uwzględnij całe wyrazy  
 Po wybraniu **Find Results** systemu windows będą wyświetlane tylko wystąpień **Znajdź** ciąg, który są dopasowywane w słowach ukończone. Na przykład wyszukiwanie "MyObject" zwróci "MyObject", ale nie "CMyObject" lub "MyObjectC."  
  
 Używanie wyrażeń regularnych  
 Gdy to pole wyboru jest zaznaczone, można użyć notacji specjalne do definiowania wzorców tekstu w **Znajdź** lub **Zamień** pól tekstowych. Aby uzyskać listę tych notacji, zobacz [za pomocą wyrażeń regularnych w programie Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).  
  
 Spójrz na następujące typy plików  
 Ta lista wskazuje typy plików, aby wyszukiwać w **przeszukania** katalogów. Jeśli to pole pozostanie puste, wszystkie pliki w **przeszukania** katalogi będą przeszukiwane.  
  
 Wybierz dowolny element na liście, aby wprowadzić wstępnie wyszukiwany ciąg, który zawiera pliki określonego typu.  
  
## <a name="result-options"></a>Opcje wyników  
 Można rozwinąć lub zwinąć **wyniku opcje** sekcji. Następujące opcje można zaznaczyć lub wyczyścić:  
  
 Znajdź wyniki 1 okno  
 Po wybraniu wyniki bieżące wyszukiwanie spowoduje zastąpienie zawartości **Znajdź wyniki 1** okna. To okno zostanie otwarty automatycznie do wyświetlenia wyników wyszukiwania. Aby ręcznie otworzyć to okno, wybierz **Windows inne** z **widoku** menu i wybierz polecenie **Znajdź wyniki 1**.  
  
 Znajdź wyniki 2 okno  
 Po wybraniu wyniki bieżące wyszukiwanie spowoduje zastąpienie zawartości **Znajdź wyniki 2** okna. To okno zostanie otwarty automatycznie do wyświetlenia wyników wyszukiwania. Aby ręcznie otworzyć to okno, wybierz **Windows inne** z **widoku** menu i wybierz polecenie **Znajdź wyniki 2**.  
  
 Wyświetl tylko nazwy pliku  
 Gdy to pole wyboru jest zaznaczone, windows Find Results listę pełne nazwy i ścieżki dla wszystkich plików, które zawierają ciąg wyszukiwania. Jednak wyniki nie uwzględniają wiersza kodu, w którym pojawia się ciąg. To pole wyboru jest dostępne dla Znajdź w plikach tylko.  
  
 Nie zamykaj modyfikowanych plików po Zamień wszystkie  
 Po wybraniu pozostawia otwarty wszystkie pliki, w których zamiany wprowadzono, dzięki czemu można cofnąć lub zapisać zmiany. Ograniczenia pamięci może ograniczać liczbę plików, które mogą pozostawać otwarte po operacji Zastąp.  
  
> [!CAUTION]
>  Możesz użyć **Cofnij** tylko na plikach, które pozostają otwarte do edycji. Jeśli ta opcja nie jest zaznaczone, pliki, które nie zostały już otworzyć do edycji pozostanie zamknięty, a nie **Cofnij** opcja będzie dostępna w tych plikach.  
  
## <a name="see-also"></a>Zobacz też  
 [Znajdowanie i zastępowanie tekstu](../ide/finding-and-replacing-text.md)   
 [Znajdź w plikach](../ide/find-in-files.md)   
 [Visual Studio — polecenia](../ide/reference/visual-studio-commands.md)
