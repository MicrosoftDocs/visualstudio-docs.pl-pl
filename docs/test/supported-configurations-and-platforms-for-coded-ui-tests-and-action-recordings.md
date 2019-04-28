---
title: Konfiguracje i platformy dla kodowanych testów interfejsu użytkownika
ms.date: 10/04/2015
ms.topic: reference
helpviewer_keywords:
- coded UI tests
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
author: gewarren
ms.openlocfilehash: 43153f86ca9ee9a26465ad910b6918aee5292a87
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62431253"
---
# <a name="supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings"></a>Obsługiwane konfiguracje oraz platformy zakodowanych testów interfejsu użytkownika i nagrywania akcji

W poniższej tabeli wymieniono obsługiwane konfiguracje i platformy dla kodowanych testów interfejsu użytkownika programu Visual Studio Enterprise. Te konfiguracje mają zastosowanie również do nagrań działań utworzonych za pomocą [!INCLUDE[MTRlong](../test/includes/mtrlong_md.md)].

> [!NOTE]
> Proces kodowanego testu interfejsu użytkownika musi mieć takie same uprawnienia, jak aplikacja poddawana testom.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Wymagania**

- Visual Studio Enterprise

## <a name="supported-configurations"></a>Obsługiwane konfiguracje

| Konfiguracja | Obsługiwane |
|-| - |
| Systemy operacyjne | [!INCLUDE[win7](../debugger/includes/win7_md.md)]<br /><br /> [!INCLUDE[winsvr08_r2](../debugger/includes/winsvr08_r2_md.md)]<br /><br /> [!INCLUDE[win8](../debugger/includes/win8_md.md)]<br /><br /> Windows 10 |
| Obsługa wersji 32-/64-bitowej | Windows 32-bitowe, w którym uruchomiono 32-bitowych [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] umożliwia przetestowanie aplikacji 32-bitowych.<br /><br /> Windows 64-bitowe, w którym uruchomiono 32-bitowych [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] przetestowanie 32-bitowych aplikacji WOW z interfejsem użytkownika Synchronization.n.<br /><br /> Windows 64-bitowe, w którym uruchomiono 32-bitowych [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] umożliwia przetestowanie 64-bitowych Windows Forms i aplikacji WPF, która nie ma interfejsu użytkownika Synchronization. |
| Architektura | x86 i x64 **Uwaga:**  Program Internet Explorer nie jest obsługiwane w trybie 64-bitowym z wyjątkiem sytuacji, gdy jest uruchomiona w [!INCLUDE[win8](../debugger/includes/win8_md.md)] lub nowszej wersji. |
| .NET | .NET 2.0, 3.0, 3.5, 4 i 4.5. **Uwaga:** [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] i programu Visual Studio będą wymagać .NET 4 do działania. Jednak aplikacje opracowane za pomocą wymienionych wersji środowiska .NET są obsługiwane. |

> [!NOTE]
> *Interfejsu użytkownika Synchronization* jest funkcją, gdzie odtwarzanie jest weryfikowane w kolejce wiadomości każdego formantu. Jeśli formant nie odpowiedział na zdarzenie, które zostało do niego wysłane, zdarzenie jest wysyłane ponownie.

## <a name="platform-support"></a>Obsługa różnych platform

| Platforma | Poziom wsparcia |
|-| - |
| Aplikacje Windows Phone | Tylko WinRT XAML na podstawie Phone aplikacje są obsługiwane. |
| Aplikacje platformy uniwersalnej systemu Windows | Obsługiwane są tylko aplikacje platformy uniwersalnej systemu Windows oparte na XAML. |
| Aplikacje uniwersalne systemu Windows | Obsługiwane są tylko XAML Universal Windows aplikacje oparte na telefon i pulpitu. |
| Krawędź | Rejestrowanie kroków akcji lub przy użyciu konstruktora, aby wyświetlić właściwości obiektu nie jest obsługiwane. Testy mogą być odtwarzane w przeglądarce Microsoft Edge, przy użyciu programu Visual Studio 2015 Update 2 i nowsze wersje [Coded UI cross rozszerzenia przeglądarki do testowania](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting). |
| Internet Explorer 8<br /><br /> Internet Explorer 9<br /><br /> Program Internet Explorer 10 **ważne:**  Przeglądarka Internet Explorer 10 jest obsługiwana tylko na komputerach stacjonarnych. <br /><br /> Program Internet Explorer 11 **ważne:**  Internet Explorer 11 jest obsługiwana tylko na pulpicie. | W pełni obsługiwane.<br /><br /> -   **Pomoc techniczna dla HTML5 w Internet Explorer 9 i Internet Explorer 10:** Kodowane testy interfejsu użytkownika obsługują rekordu, odtwarzanie i sposób sprawdzania poprawności formantów HTML5: Dźwięk, wideo, pasek postępu i suwak. Aby uzyskać więcej informacji, zobacz [HTML5 za pomocą kontrolki w kodowanych testów interfejsu użytkownika](../test/using-html5-controls-in-coded-ui-tests.md). **Ostrzeżenie:**      Jeśli tworzysz kodowane testy interfejsu użytkownika w Internet Explorer 10, mogą one nie zostać uruchomione w Internet Explorer 9 i Internet Explorer 8. Jest to spowodowane tym, że Internet Explorer 10 zawiera formanty HTML5, takie jak audio, wideo, pasek postępu i suwak. Te formanty HTML5 nie są rozpoznawane przez Internet Explorer 9 i Internet Explorer 8. Podobnie test interfejsu użytkownika kodowany za pomocą Internet Explorer 9 może zawierać niektóre formanty języka HTML5, które również nie zostaną rozpoznane przez Internet Explorer 8.<br />-   **Obsługa Internetu sprawdzanie pisowni Explorer 10:** Internet Explorer 10 zawiera funkcję sprawdzania pisowni dla wszystkich pól tekstowych. Pozwala to na wybranie z listy sugerowanych poprawek. Kodowany test interfejsu użytkownika będzie ignorować czynności użytkownika, takie jak zaznaczenie sugestii alternatywnej pisowni. Rejestrowany będzie tylko końcowy tekst wpisany w polu tekstowym.<br />     Następujące akcje są rejestrowane dla kodowanego testu interfejsu użytkownika które używają formantu sprawdzania pisowni: Dodaj do słownika, Kopiuj, zaznacz wszystko, Dodaj do słownika i Ignoruj.<br />-   **Obsługa 64-bitowej przeglądarki Internet Explorer uruchomionej w systemie Windows 8:** 64-bitowych wersjach programu Internet Explorer nie były wcześniej obsługiwane dla nagrywania i odtwarzania. Za pomocą [!INCLUDE[win8](../debugger/includes/win8_md.md)] i [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)], kodowane testy interfejsu użytkownika zostały włączone dla 64-bitowych wersjach programu Internet Explorer. **Ostrzeżenie:**      Obsługa 64-bitowego programu Internet Explorer stosuje się tylko po uruchomieniu [!INCLUDE[win8](../debugger/includes/win8_md.md)] lub nowszej.<br />-   **Obsługa przypiętych witryn w przeglądarce Internet Explorer 9:** W programie Internet Explorer 9 wprowadzono przypięte witryny. Dzięki przypiętym witrynom można przejść do ulubionych witryn bezpośrednio z paska zadań systemu Windows — bez konieczności wcześniejszego otwierania Internet Explorer. Kodowane testy interfejsu użytkownika mogą teraz świadomie generować akcje na przypiętych witrynach. Aby uzyskać więcej informacji na temat przypiętych witryn, zobacz [przypięte witryny](http://go.microsoft.com/fwlink/?LinkId=220037).<br />-   **Pomoc techniczna dla znaczniki semantyczne programu Internet Explorer 9:** Internet Explorer 9 wprowadzono następujące znaczniki semantyczne: sekcja, nav, artykuł, aside, hgroup, nagłówek, stopka, rysunek, figcaption i mark. Kodowane testy interfejsu użytkownika ignorują wszystkie te znaczniki semantyczne podczas nagrywania. Możesz dodać potwierdzenia na tych tagach za pomocą Konstruktora kodowanego testu interfejsu użytkownika. Można użyć pokrętła nawigacji w Konstruktorze kodowanego testu interfejsu użytkownika, aby nawigować do jednego z tych elementów i przeglądać ich właściwości.<br />-   **Bezproblemowa obsługa białych znaków między wersjami programu Internet Explorer:** Istnieją różnice w zakresie obsługi znaków odstępu między Internet Explorer 8, Internet Explorer 9 i Internet Explorer 10. Kodowany test interfejsu użytkownika bezproblemowo obsługuje te różnice. Dlatego kodowany test interfejsu użytkownika, utworzony na przykład w Internet Explorer 8, będzie z powodzeniem odtwarzany w Internet Explorer 9 i Internet Explorer 10.<br />-   **Obszar powiadomień Internet Explorer są teraz rejestrowane z zestawem atrybutów "Kontynuuj przy błędzie":** Wszystkie akcje w obszarze powiadomień programu Internet Explorer są teraz rejestrowane z zestawem atrybutów "Kontynuuj po błędzie". Jeśli nie ma paska powiadomień podczas odtwarzania, operacje na nim zostaną zignorowane i kodowany test interfejsu użytkownika przejdzie do następnej akcji. |
| Formanty Windows Forms i WPF innych firm | W pełni obsługiwane.<br /><br /> Aby włączyć formanty innych firm w formularzach Windows Forms i aplikacjach WPF, należy dodać odwołania i kod. Aby uzyskać więcej informacji, zobacz [Włącz testowanie kodowanego interfejsu użytkownika dla kontrolek](../test/enable-coded-ui-testing-of-your-controls.md). |
| Internet Explorer 6<br /><br /> Internet Explorer 7 | Nieobsługiwane. |
| Chrome<br /><br /> Firefox | Rejestrowanie czynności nie jest obsługiwane. Zakodowane testy interfejsu użytkownika mogą być odtwarzane w przeglądarkach Chrome i Firefox z programu Visual Studio 2012 aktualizacja 4 lub nowsza. Przejdź [tutaj](using-different-web-browsers-with-coded-ui-tests.md) Aby uzyskać więcej informacji. |
| Opera<br /><br /> Safari | Nieobsługiwane. |
| Silverlight | Nieobsługiwane.<br /><br /> Dla programu Visual Studo 2013, możesz pobrać [Microsoft Visual Studio 2013 kodowanego wtyczka testowania interfejsu użytkownika dla programu Silverlight](https://go.microsoft.com/fwlink/?LinkId=691026) z galerii Visual Studio. |
| Flash/Java | Nieobsługiwane. |
| Windows Forms 2.0 i nowsze wersje | W pełni obsługiwane. **Uwaga:**  Formanty NetFx są w pełni obsługiwane, ale nie wszystkie formanty innych firm są obsługiwane. |
| WPF 3.5 i nowsze wersje | W pełni obsługiwane.<br /><br /> **Uwaga** formanty NetFx są w pełni obsługiwane, ale nie wszystkie formanty innych firm są obsługiwane. |
| Windows Win32 | Może pracować z niektórymi znanymi problemami, ale nie jest oficjalnie obsługiwany. |
| MFC | Obsługiwane częściowo. Zobacz [UITest framework](https://blogs.msdn.microsoft.com/vstsqualitytools/2010/04/15/uitest-framework-mfc-support-in-vs-2010/) Aby uzyskać szczegółowe informacje, jakie funkcje są obsługiwane. |
| Program SharePoint | W pełni obsługiwane. |
| Aplikacje klienckie pakietu Office | Nieobsługiwane. |
| Klient sieci web Dynamics CRM | W pełni obsługiwane. |
| Klient Dynamics (Ax) 2012 | Akcje odtwarzania i nagrywania są obsługiwane częściowo. Zobacz [Visual Studio 10 kodowanego interfejsu użytkownika / nagrań akcji pomocy technicznej dla oprogramowania Microsoft Dynamics](https://blogs.msdn.microsoft.com/dave_froslie/2011/09/01/visual-studio-10-coded-ui-action-recordings-support-for-microsoft-dynamics-ax-2012/) Aby uzyskać szczegółowe informacje. |
| SAP | Nieobsługiwane. |
| Citrix/usługi terminalowe | Rejestrowanie czynności na serwerze terminali nie jest zalecane. Rejestrator nie obsługuje uruchamianie wielu wystąpień w tym samym czasie. |
| PowerBuilder | Obsługiwane częściowo.<br /><br /> Obsługa zakresu ułatwień dostępu jest włączona dla formantów PowerBuilder. |

 Aby uzyskać informacje dotyczące sposobu tworzenia rozszerzeń do obsługi innych platform, zobacz [Włącz testowanie kodowanego interfejsu użytkownika dla kontrolek](../test/enable-coded-ui-testing-of-your-controls.md) i [rozszerzanie kodowanych testów interfejsu użytkownika i nagrywania akcji](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md).

## <a name="see-also"></a>Zobacz także

- [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)
