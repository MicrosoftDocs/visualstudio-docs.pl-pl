---
title: Najlepsze praktyki dotyczące kodowanych testów interfejsu użytkownika | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests, best practices
ms.assetid: d5aef766-a24c-4f1f-ac9b-e5462b6627d4
caps.latest.revision: 41
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 37e0ae51589d85ac52ec962fb3cb193fc37a7ad4
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68147904"
---
# <a name="best-practices-for-coded-ui-tests"></a>Najlepsze praktyki dotyczące kodowanych testów interfejsu użytkownika
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

W tym temacie opisano najlepsze rozwiązania, które należy wykonać podczas tworzenia kodowanych testów interfejsu użytkownika.  
  
 **Wymagania**  
  
- Visual Studio Enterprise  
  
## <a name="best-practices"></a>Najlepsze praktyki  
 Skorzystaj z poniższych wskazówek do tworzenia elastycznych kodowanego testu interfejsu użytkownika.  
  
- Użyj **kodowanego testu interfejsu użytkownika** zawsze, gdy jest to możliwe.  
  
- Nie należy modyfikować `UIMap.designer.cs` pliku bezpośrednio. Jeśli to zrobisz, zmiany w pliku zostaną zastąpione.  
  
- Utwórz test jako sekwencja zarejestrowane metody. Aby uzyskać więcej informacji o sposobie rejestrowania metody, zobacz [tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate).  
  
- Każda metoda zarejestrowane powinna działać na jednej stronie, formularza lub okno dialogowe. Utworzenie nowej metody testów dla każdej nowej strony, formularza lub okno dialogowe.  
  
- Podczas tworzenia metody należy użyć nazwy metody istotnych zamiast domyślnej nazwy. Znaczącą nazwę pomaga w identyfikacji przeznaczenia metody.  
  
- Jeśli to możliwe, należy ograniczyć każdego nagraną metodę do mniej niż 10 akcji. To podejście modułowej ułatwia zastąpić metodę, jeśli zmieni się interfejs użytkownika.  
  
- Tworzenie przy użyciu każdego potwierdzenia **kodowanego testu interfejsu użytkownika**, która automatycznie dodaje metodę potwierdzenie `UIMap.Designer.cs` pliku.  
  
- Jeśli zmieni się interfejs użytkownika (UI), ponownie zarejestrować metod testowych lub metody asercji, lub ponownie zarejestrować poszczególnych sekcjach istniejącej metody testowej.  
  
- Utwórz osobne <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> pliku dla każdego modułu w testowanej aplikacji. Aby uzyskać więcej informacji, zobacz [testowanie dużej aplikacji przy użyciu wielu map UI](../test/testing-a-large-application-with-multiple-ui-maps.md).  
  
- W testowanej aplikacji, użyj nazw opisowych, podczas tworzenia kontrolek interfejsu użytkownika. Dzięki temu więcej znaczenia i użyteczność nazw automatycznie wygenerowanego formantu.  
  
- Jeśli tworzysz potwierdzenia od kodowania za pomocą interfejsu API, należy utworzyć metodę dla każdego potwierdzenia w części <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap> klasę, która znajduje się w `UIMap.cs` pliku. Wywołaj tę metodę ze swojej metody testowej, można wykonać potwierdzenia.  
  
- Jeśli bezpośrednio kodują przy użyciu interfejsu API, użyj właściwości i metod w klasach wygenerowane w `UIMap.Designer.cs` pliku w kodzie, jak możesz. W ramach tych zajęć ułatwi pracę, łatwiejsze i bardziej niezawodne i pomoże Ci osiągnąć bardziej produktywne.  
  
  Kodowane testy interfejsu użytkownika automatycznie dostosowywać się do wielu zmian w interfejsie użytkownika. Jeśli na przykład element interfejsu użytkownika został zmieniony, położenie i kolor, w większości przypadków kodowanego testu interfejsu użytkownika będą nadal znaleźć poprawny element.  
  
  Podczas przebiegu testu, kontrolek interfejsu użytkownika znajduje się struktura testowania przy użyciu zestawu właściwości wyszukiwania, które są stosowane do każdej klasy formantu w definicjach utworzone przez **Konstruktor kodowanego testu IU** w `UIMap.Designer.cs` pliku. Właściwości wyszukiwania zawierają pary nazwa / wartość nazw właściwości i wartości właściwości, które mogą służyć do identyfikowania kontrolki, takie jak <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.FriendlyName%2A>, <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.Name%2A>, i <xref:Microsoft.VisualStudio.TestTools.UITesting.UITestControl.ControlType%2A> właściwości formantu. Jeśli właściwości wyszukiwania nie ulegną zmianie, kodowany test interfejsu użytkownika pomyślnie odnaleźć formantu w interfejsie użytkownika. Zmiana właściwości wyszukiwania kodowane testy interfejsu użytkownika ma algorytm inteligentnego dopasowania, stosowany Algorytm heurystyczny w celu znalezienia kontrolek i systemu windows w interfejsie użytkownika. Gdy interfejs użytkownika został zmieniony, może być zmodyfikowanie właściwości wyszukiwania wcześniej zdefiniowane elementy, aby upewnić się, że zostaną znalezione.  
  
## <a name="what-to-do-if-your-user-interface-changes"></a>Co zrobić, jeśli zmieni się interfejs użytkownika  
 Interfejsy użytkownika, która jest często zmieniać podczas programowania. Oto kilka sposobów, aby zmniejszyć wpływ tych zmian:  
  
- Znajdź nagraną metodę, która odwołuje się do tego formantu i użyj **kodowanego testu interfejsu użytkownika** do ponownego rejestrowania akcji dla tej metody. Taką samą nazwę dla metody umożliwia zastąpienie istniejących działań.  
  
- Jeśli w kontrolce wystąpi potwierdzenie, że nie jest już prawidłowy:  
  
  - Usuń metodę, która zawiera potwierdzenie.  
  
  - Usuń wywołanie tej metody z metody testowej.  
  
  - Dodawanie nowej asercji przeciągając przycisk krzyżyka do kontrolki interfejsu użytkownika, otwórz mapę interfejsu użytkownika i Dodaj nowe potwierdzenie.  
  
  Aby uzyskać więcej informacji na temat sposobu rejestrowania kodowane testy interfejsu użytkownika, zobacz [Użyj interfejsu użytkownika do testów Your kodu automatyzacji](../test/use-ui-automation-to-test-your-code.md).  
  
## <a name="what-to-do-if-a-background-process-needs-to-complete-before-the-test-can-continue"></a>Co należy zrobić, jeśli proces w tle musi wykonać, zanim będzie można kontynuować test  
 Trzeba będzie poczekać, aż do zakończenia procesu, przed kontynuowaniem do następnej akcji interfejsu użytkownika. Można użyć w tym celu <xref:Microsoft.VisualStudio.TestTools.UITesting.PlaybackSettings.WaitForReadyLevel%2A> oczekiwania na zakończenie testu będzie kontynuowane tak jak w następującym przykładzie.  
  
```  
// Set the playback to wait for all threads to finish  
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.AllThreads;  
  
// Press the submit button  
this.UIMap.ClickSubmit();  
  
// Reset the playback to wait only for the UI thread to finish  
Playback.PlaybackSettings.WaitForReadyLevel = WaitForReadyLevel.UIThreadOnly;  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualStudio.TestTools.UITest.Common.UIMap.UIMap>   
 <xref:Microsoft.VisualStudio.TestTools.UITesting>   
 [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)   
 [Tworzenie kodowanych testów interfejsu użytkownika](../test/use-ui-automation-to-test-your-code.md#VerifyingCodeUsingCUITCreate)   
 [Testowanie dużej aplikacji przy użyciu wielu map UI](../test/testing-a-large-application-with-multiple-ui-maps.md)   
 [Obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i rejestrowania akcji](../test/supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings.md)
