---
title: Obsługiwane konfiguracje i platformy dla kodowanych testów interfejsu użytkownika i nagrań akcji | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-test
ms.topic: conceptual
helpviewer_keywords:
- coded UI tests
ms.assetid: 544742b5-4ec1-4d51-b941-72b2f6ff17bc
caps.latest.revision: 108
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 147c15baf8f089bf41262e04694bce8b5b44f31e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72660417"
---
# <a name="supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings"></a>Obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i nagrywania akcji
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Obsługiwane konfiguracje i platformy dla kodowanych testów interfejsu użytkownika dla Visual Studio Enterprise są wymienione w poniższej tabeli. Te konfiguracje mają zastosowanie również do nagrań akcji utworzonych przy użyciu [!INCLUDE[MTRlong](../includes/mtrlong-md.md)].

> [!NOTE]
> Proces kodowanego testu interfejsu użytkownika musi mieć takie same uprawnienia, jak aplikacja poddawana testom.

 **Requirements**

- Visual Studio Enterprise

## <a name="supported-configurations"></a>Obsługiwane konfiguracje

|Konfiguracja|Obsługiwane|
|-------------------|---------------|
|Systemy operacyjne|[!INCLUDE[win7](../includes/win7-md.md)]<br /><br /> [!INCLUDE[winsvr08_r2](../includes/winsvr08-r2-md.md)]<br /><br /> [!INCLUDE[win8](../includes/win8-md.md)]<br /><br /> Windows 10|
|Obsługa wersji 32-/64-bitowej|32-bitowy system Windows z systemem 32-bitowym [!INCLUDE[TCMext](../includes/tcmext-md.md)] może testować aplikacje 32-bitowe.<br /><br /> 64-bitowy system Windows z systemem 32-bitowym [!INCLUDE[TCMext](../includes/tcmext-md.md)] może testować 32-bitowe aplikacje WOW z interfejsem użytkownika Synchronization. n.<br /><br /> 64-bitowy system Windows z systemem 32-bitowym [!INCLUDE[TCMext](../includes/tcmext-md.md)] może testować 64-bitowe Windows Forms i aplikacje WPF, które nie mają synchronizacji interfejsu użytkownika.|
|Architektura|**Uwaga dotycząca** architektury x86 i x64: program Internet Explorer nie jest obsługiwany w trybie 64-bitowym, z wyjątkiem sytuacji, w których jest uruchomiony w [!INCLUDE[win8](../includes/win8-md.md)] lub nowszych wersjach.|
|.NET|.NET 2.0, 3.0, 3.5, 4 i 4.5. **Uwaga:** [!INCLUDE[TCMext](../includes/tcmext-md.md)] i Visual Studio będą wymagały działania programu .NET 4. Jednak aplikacje opracowane za pomocą wymienionych wersji środowiska .NET są obsługiwane.|

> [!NOTE]
> *Synchronizacja interfejsu użytkownika* to funkcja, w której odtwarzanie jest weryfikowane w kolejce wiadomości każdej kontrolki. Jeśli formant nie odpowiedział na zdarzenie, które zostało do niego wysłane, zdarzenie jest wysyłane ponownie.

## <a name="platform-support"></a>Obsługa platformy

|Platforma|Poziom wsparcia|
|--------------|----------------------|
|Aplikacje Windows Phone|Obsługiwane są tylko aplikacje dla telefonów opartych na języku WinRT-XAML.|
|Aplikacje Windows Store|Obsługiwane są tylko aplikacje do Sklepu oparte na języku XAML.|
|Aplikacje uniwersalne systemu Windows|Obsługiwane są tylko aplikacje uniwersalne systemu Windows oparte na języku XAML na telefonie i pulpicie.|
|Krawędź|W programie Visual Studio 2015 Update 2 i nowszych za pomocą [rozszerzenia kodowanego przetestowania między przeglądarkami interfejsu użytkownika](https://visualstudiogallery.msdn.microsoft.com/11cfc881-f8c9-4f96-b303-a2780156628d)|
|Internet Explorer 8<br /><br /> Internet Explorer 9<br /><br /> Ważne w programie Internet Explorer 10 **:** program Internet Explorer 10 jest obsługiwany tylko na pulpicie. <br /><br /> Internet Explorer 11 **Ważne:** program Internet Explorer 11 jest obsługiwany tylko na pulpicie.|W pełni obsługiwane.<br /><br /> -   **Obsługa języka HTML5 w programie Internet Explorer 9 i Internet Explorer 10:** kodowane testy interfejsu użytkownika obsługują rejestrowanie, odtwarzanie i sprawdzanie poprawności formantów HTML5: audio, wideo, ProgressBar i Slider. Aby uzyskać więcej informacji, zobacz [Korzystanie z kontrolek HTML5 w kodowanych testach interfejsu użytkownika](../test/using-html5-controls-in-coded-ui-tests.md). **Ostrzeżenie:**      Jeśli utworzysz kodowane testy interfejsu użytkownika w programie Internet Explorer 10, mogą one nie działać w programie Internet Explorer 9 lub Internet Explorer 8. Jest to spowodowane tym, że Internet Explorer 10 zawiera formanty HTML5, takie jak audio, wideo, pasek postępu i suwak. Te formanty HTML5 nie są rozpoznawane przez Internet Explorer 9 i Internet Explorer 8. Podobnie test interfejsu użytkownika kodowany za pomocą Internet Explorer 9 może zawierać niektóre formanty języka HTML5, które również nie zostaną rozpoznane przez Internet Explorer 8.<br />-   **Obsługa sprawdzania pisowni w programie Internet Explorer 10:** program Internet Explorer 10 zawiera możliwości sprawdzania pisowni dla wszystkich pól tekstowych. Pozwala to na wybranie z listy sugerowanych poprawek. Kodowany test interfejsu użytkownika będzie ignorować czynności użytkownika, takie jak zaznaczenie sugestii alternatywnej pisowni. Rejestrowany będzie tylko końcowy tekst wpisany w polu tekstowym.<br />     Następujące akcje są rejestrowane dla kodowanych testów interfejsu użytkownika, które używają formantu sprawdzania pisowni: Dodaj do słownika, Kopiuj, Zaznacz wszystko, Dodaj do słownika i Ignoruj.<br />**obsługa -    64-bitowego programu Internet Explorer działającego w systemie Windows 8:** wcześniej, 64-bitowe wersje programu Internet Explorer nie były obsługiwane w przypadku nagrywania i odtwarzania. W przypadku [!INCLUDE[win8](../includes/win8-md.md)] i [!INCLUDE[vs_dev11_long](../includes/vs-dev11-long-md.md)], kodowane testy interfejsu użytkownika zostały włączone dla 64-bitowych wersji programu Internet Explorer. **Ostrzeżenie:** 64-bitowe wsparcie dla programu Internet Explorer ma zastosowanie tylko wtedy, gdy korzystasz z programu [!INCLUDE[win8](../includes/win8-md.md)] lub nowszego.<br />-   **Obsługa przypiętych witryn w programie Internet Explorer 9:** w programie Internet Explorer 9 wprowadzono przypięte witryny. Dzięki przypiętym witrynom można przejść do ulubionych witryn bezpośrednio z paska zadań systemu Windows — bez konieczności wcześniejszego otwierania Internet Explorer. Kodowane testy interfejsu użytkownika mogą teraz świadomie generować akcje na przypiętych witrynach. Aby uzyskać więcej informacji na temat przypiętych witryn, zobacz [przypięte witryny](http://go.microsoft.com/fwlink/?LinkId=220037).<br />**obsługa -    dla tagów semantycznych programu Internet Explorer 9:** program Internet Explorer 9 wprowadził następujące znaczniki semantyczne: sekcja, NAV, artykuł, hgroup, nagłówek, stopka, rysunek, figcaption i Mark. Kodowane testy interfejsu użytkownika ignorują wszystkie te znaczniki semantyczne podczas nagrywania. Możesz dodać potwierdzenia na tych tagach za pomocą Konstruktora kodowanego testu interfejsu użytkownika. Można użyć pokrętła nawigacji w Konstruktorze kodowanego testu interfejsu użytkownika, aby nawigować do jednego z tych elementów i przeglądać ich właściwości.<br />-   **bezproblemową obsługę białych znaków między wersjami programu Internet Explorer:** istnieją różnice w obsłudze białych znaków między Internet Explorer 8, Internet Explorer 9 i Internet Explorer 10. Kodowany test interfejsu użytkownika bezproblemowo obsługuje te różnice. Dlatego kodowany test interfejsu użytkownika, utworzony na przykład w Internet Explorer 8, będzie z powodzeniem odtwarzany w Internet Explorer 9 i Internet Explorer 10.<br />-   **obszarze powiadomień programu Internet Explorer są teraz rejestrowane z ustawionym zestawem atrybutów "Kontynuuj po błędzie":** wszystkie akcje w obszarze powiadomień programu Internet Explorer są teraz rejestrowane z ustawionym zestawem atrybutów "Kontynuuj po błędzie". Jeśli nie ma paska powiadomień podczas odtwarzania, operacje na nim zostaną zignorowane i kodowany test interfejsu użytkownika przejdzie do następnej akcji.|
|Formanty Windows Forms i WPF innych firm|W pełni obsługiwane.<br /><br /> Aby włączyć formanty innych firm w formularzach Windows Forms i aplikacjach WPF, należy dodać odwołania i kod. Aby uzyskać więcej informacji, zobacz [Włączanie testowania kodowanego interfejsu użytkownika dla kontrolek](../test/enable-coded-ui-testing-of-your-controls.md).|
|Internet Explorer 6<br /><br /> Internet Explorer 7|Nieobsługiwane.|
|Chrome<br /><br /> Firefox|Rejestrowanie czynności nie jest obsługiwane. Zakodowane testy interfejsu użytkownika mogą być odtwarzane w przeglądarkach Chrome i Firefox z programu Visual Studio 2012 aktualizacja 4 lub nowsza. Przejdź [tutaj](https://msdn.microsoft.com/library/jj835758.aspx) , aby uzyskać więcej szczegółów.|
|Opera<br /><br /> Safari|Nieobsługiwane.|
|Silverlight|Nieobsługiwane.<br /><br /> W przypadku programu Visual Studo 2013 można jednak pobrać [wtyczkę kodowanego testu interfejsu użytkownika Microsoft Visual Studio 2013 dla programu Silverlight](https://go.microsoft.com/fwlink/?LinkId=691026) z galerii programu Visual Studio.|
|Flash/Java|Nieobsługiwane.|
|Windows Forms 2.0 i nowsze wersje|W pełni obsługiwane. **Uwaga:**  Formanty NetFx są w pełni obsługiwane, ale nie wszystkie formanty innych firm są obsługiwane.|
|WPF 3.5 i nowsze wersje|W pełni obsługiwane.<br /><br /> **Uwaga** Formanty NetFx są w pełni obsługiwane, ale nie wszystkie formanty innych firm są obsługiwane.|
|Windows Win32|Może pracować z niektórymi znanymi problemami, ale nie jest oficjalnie obsługiwany.|
|MFC|Obsługiwane częściowo. Zobacz następującą [witrynę sieci Web firmy Microsoft](http://go.microsoft.com/fwlink/?LinkId=206511) , aby uzyskać szczegółowe informacje o obsługiwanych funkcjach.|
|Program SharePoint|W pełni obsługiwane.|
|Aplikacje klienckie pakietu Office|Nieobsługiwane.|
|Klient sieci web Dynamics CRM|W pełni obsługiwane.|
|Klient Dynamics (Ax) 2012|Akcje odtwarzania i nagrywania są obsługiwane częściowo. Aby uzyskać szczegółowe informacje, zobacz następującą [witrynę sieci Web firmy Microsoft](http://go.microsoft.com/fwlink/?LinkId=232677) .|
|SAP|Nieobsługiwane.|
|Citrix/usługi terminalowe|Nie zalecamy rejestrowania akcji na serwerze terminali. Rejestrator nie obsługuje jednoczesnego uruchamiania wielu wystąpień.|
|PowerBuilder|Obsługiwane częściowo.<br /><br /> Obsługa zakresu ułatwień dostępu jest włączona dla formantów PowerBuilder.|

 Aby uzyskać informacje dotyczące sposobu tworzenia rozszerzeń do obsługi innych platform, zobacz [Włącz kodowane testy interfejsu użytkownika dla kontrolek](../test/enable-coded-ui-testing-of-your-controls.md) i [rozszerzanie KODOWANYCH testów interfejsu użytkownika i nagrań akcji do obsługi programu Microsoft Excel](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md).

## <a name="see-also"></a>Zobacz też
 [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md) [generującego KODOWANY test interfejsu użytkownika z istniejącego rejestrowania akcji](https://msdn.microsoft.com/library/56736963-9027-493b-b5c4-2d4e86d1d497)
