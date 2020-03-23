---
title: Konfiguracje i platformy dla kodowanych testów interfejsu użytkownika
ms.date: 10/04/2015
ms.topic: reference
helpviewer_keywords:
- coded UI tests
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: e18e50537f35080f9796f4a090b3806953ae5170
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75845811"
---
# <a name="supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings"></a>Obsługiwane konfiguracje i platformy dla zakodowanych testów interfejsu użytkownika i nagrań akcji

Obsługiwane konfiguracje i platformy dla kodowanych testów interfejsu użytkownika dla programu Visual Studio Enterprise są wymienione w poniższej tabeli. Te konfiguracje dotyczą również nagrań [!INCLUDE[MTRlong](../test/includes/mtrlong_md.md)]akcji utworzonych za pomocą programu .

> [!NOTE]
> Proces kodowanego testu interfejsu użytkownika musi mieć takie same uprawnienia, jak aplikacja poddawana testom.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Wymagania**

- Visual Studio Enterprise

## <a name="supported-configurations"></a>Obsługiwane konfiguracje

| Konfigurowanie | Obsługiwane |
|-| - |
| Systemy operacyjne | [!INCLUDE[win7](../debugger/includes/win7_md.md)]<br /><br /> [!INCLUDE[winsvr08_r2](../debugger/includes/winsvr08_r2_md.md)]<br /><br /> [!INCLUDE[win8](../debugger/includes/win8_md.md)]<br /><br /> Windows 10 |
| Obsługa wersji 32-/64-bitowej | 32-bitowy system Windows z systemem [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] 32-bitowym może testować aplikacje 32-bitowe.<br /><br /> 64-bitowy system Windows z systemem [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] 32-bitowym może testować 32-bitowe aplikacje WOW, które mają interfejs synchronizacji interfejsu użytkownika.n.<br /><br /> 64-bitowy system Windows z uruchomionym 32-bitowym [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] systemem Windows może testować 64-bitowe formularze systemu Windows i aplikacje WPF, które nie mają synchronizacji interfejsu użytkownika. |
| Architektura | x86 i x64 **Uwaga:** Program Internet Explorer nie jest obsługiwany w [!INCLUDE[win8](../debugger/includes/win8_md.md)] trybie 64-bitowym, z wyjątkiem sytuacji, gdy jest uruchomiony w wersjach poniżej lub nowszych. |
| .NET | .NET 2.0, 3.0, 3.5, 4 i 4.5. **Uwaga:** [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] i Visual Studio będzie wymagać .NET 4 do działania.   Jednak aplikacje opracowane za pomocą wymienionych wersji środowiska .NET są obsługiwane. |

> [!NOTE]
> *Synchronizacja interfejsu użytkownika* to funkcja, w której odtwarzanie jest weryfikowane w kolejce komunikatów każdego formantu. Jeśli formant nie odpowiedział na zdarzenie, które zostało do niego wysłane, zdarzenie jest wysyłane ponownie.

## <a name="platform-support"></a>Obsługa platform

| Platforma | Poziom wsparcia |
|-| - |
| Aplikacje dla systemu Windows Phone | Obsługiwane są tylko aplikacje na telefon oparte na języku WinRT-XAML. |
| Aplikacje platformy UWP | Obsługiwane są tylko aplikacje platformy uniwersalnej systemu Windows oparte na języku XAML. |
| Aplikacje uniwersalne systemu Windows | Obsługiwane są tylko uniwersalne aplikacje systemu Windows oparte na języku XAML na telefon i pulpit. |
| Brzeg | Rejestrowanie kroków akcji lub używanie konstruktora do wyświetlania właściwości obiektów nie jest obsługiwane. Testy można odtwarzać w przeglądarce Edge przy użyciu programu Visual Studio 2015 Update 2 i nowszych wersji przy użyciu [rozszerzenia testowania przeglądarki kodowany interfejs użytkownika.](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting) |
| Internet Explorer 8<br /><br /> Internet Explorer 9<br /><br /> Internet Explorer 10 **Ważne:** Program Internet Explorer 10 jest obsługiwany tylko na pulpicie. <br /><br /> Internet Explorer 11 **Ważne:** Program Internet Explorer 11 jest obsługiwany tylko na pulpicie. | W pełni obsługiwane.<br /><br /> -   **Obsługa html5 w programach Internet Explorer 9 i Internet Explorer 10:** Kodowane testy interfejsu użytkownika obsługują rekord, odtwarzanie i sprawdzanie poprawności formantów HTML5: Audio, Video, ProgressBar i Slider. Aby uzyskać więcej informacji, zobacz [Używanie formantów HTML5 w kodowanych testach interfejsu użytkownika](../test/using-html5-controls-in-coded-ui-tests.md). **Ostrzeżenie:**      Jeśli w programie Internet Explorer 10 utworzysz kodowane testy interfejsu użytkownika, może on nie zostać uruchomiony przy użyciu programu Internet Explorer 9 lub Internet Explorer 8. Jest to spowodowane tym, że Internet Explorer 10 zawiera formanty HTML5, takie jak audio, wideo, pasek postępu i suwak. Te formanty HTML5 nie są rozpoznawane przez Internet Explorer 9 i Internet Explorer 8. Podobnie test interfejsu użytkownika kodowany za pomocą Internet Explorer 9 może zawierać niektóre formanty języka HTML5, które również nie zostaną rozpoznane przez Internet Explorer 8.<br />-   **Obsługa sprawdzania pisowni w programie Internet Explorer 10:** Program Internet Explorer 10 zawiera funkcje sprawdzania pisowni dla wszystkich pól tekstowych. Pozwala to na wybranie z listy sugerowanych poprawek. Kodowany test interfejsu użytkownika będzie ignorować czynności użytkownika, takie jak zaznaczenie sugestii alternatywnej pisowni. Rejestrowany będzie tylko końcowy tekst wpisany w polu tekstowym.<br />     Następujące akcje są rejestrowane dla kodowanych testów interfejsu użytkownika, które używają formantu sprawdzania pisowni: Dodaj do słownika, Kopiuj, Zaznacz wszystko, Dodaj do słownika i Ignoruj.<br />-   **Obsługa 64-bitowego programu Internet Explorer działającego w systemie Windows 8:** Wcześniej 64-bitowe wersje programu Internet Explorer nie były obsługiwane do nagrywania i odtwarzania. Z [!INCLUDE[win8](../debugger/includes/win8_md.md)] [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)]i , kodowane testy interfejsu użytkownika zostały włączone dla 64-bitowych wersji programu Internet Explorer. **Ostrzeżenie:** 64-bitowa obsługa programu Internet Explorer [!INCLUDE[win8](../debugger/includes/win8_md.md)] ma zastosowanie tylko wtedy, gdy jest uruchomiona lub później.<br />-   **Obsługa przypiętych witryn w programie Internet Explorer 9:** W programie Internet Explorer 9 wprowadzono przypięte witryny. Dzięki przypiętym witrynom można przejść do ulubionych witryn bezpośrednio z paska zadań systemu Windows — bez konieczności wcześniejszego otwierania Internet Explorer. Kodowane testy interfejsu użytkownika mogą teraz świadomie generować akcje na przypiętych witrynach. Aby uzyskać więcej informacji o przypiętych witrynach, zobacz [Przypięte witryny](https://support.microsoft.com/hub/4230784/internet-explorer-help).<br />-   **Obsługa tagów semantycznych programu Internet Explorer 9:** W programie Internet Explorer 9 wprowadzono następujące znaczniki semantyczne: sekcja, nav, artykuł, bok, hgroup, nagłówek, stopka, rysunek, figcaption i znak. Kodowane testy interfejsu użytkownika ignorują wszystkie te znaczniki semantyczne podczas nagrywania. Możesz dodać potwierdzenia na tych tagach za pomocą Konstruktora kodowanego testu interfejsu użytkownika. Można użyć pokrętła nawigacji w Konstruktorze kodowanego testu interfejsu użytkownika, aby nawigować do jednego z tych elementów i przeglądać ich właściwości.<br />-   **Bezproblemowa obsługa znaków odstępu między wersjami programu Internet Explorer:** Istnieją różnice w obsłudze znaków odstępu między programami Internet Explorer 8, Internet Explorer 9 i Internet Explorer 10. Kodowany test interfejsu użytkownika bezproblemowo obsługuje te różnice. Dlatego kodowany test interfejsu użytkownika, utworzony na przykład w Internet Explorer 8, będzie z powodzeniem odtwarzany w Internet Explorer 9 i Internet Explorer 10.<br />-   **Obszar powiadomień programu Internet Explorer są teraz rejestrowane z "Kontynuuj na błąd" Zestaw atrybutów:** Wszystkie akcje w obszarze powiadomień programu Internet Explorer są teraz rejestrowane z zestawem atrybutów "Kontynuuj na błędzie". Jeśli nie ma paska powiadomień podczas odtwarzania, operacje na nim zostaną zignorowane i kodowany test interfejsu użytkownika przejdzie do następnej akcji. |
| Formanty Windows Forms i WPF innych firm | W pełni obsługiwane.<br /><br /> Aby włączyć formanty innych firm w formularzach Windows Forms i aplikacjach WPF, należy dodać odwołania i kod. Aby uzyskać więcej informacji, zobacz [Włączanie kodowanych testów interfejsu użytkownika formantów](../test/enable-coded-ui-testing-of-your-controls.md). |
| Program Internet Explorer 6<br /><br /> Internet Explorer 7 | Bez pomocy technicznej. |
| Chrome<br /><br /> Firefox | Rejestrowanie czynności nie jest obsługiwane. Zakodowane testy interfejsu użytkownika mogą być odtwarzane w przeglądarkach Chrome i Firefox z programu Visual Studio 2012 aktualizacja 4 lub nowsza. Przejdź [tutaj,](using-different-web-browsers-with-coded-ui-tests.md) aby uzyskać więcej informacji. |
| Opera<br /><br /> Safari | Bez pomocy technicznej. |
| Silverlight | Bez pomocy technicznej.<br /><br /> W przypadku programu Visual Studo 2013 można jednak pobrać [z galerii programu Visual Studio 2013 zakodowany w programie Microsoft Visual Studio 2013 wtyczkę testową interfejsu użytkownika dla programu Silverlight.](https://marketplace.visualstudio.com/items?itemName=PrachiBoraMSFT.MicrosoftVisualStudio2013CodedUITestPluginforSilve) |
| Flash/Java | Bez pomocy technicznej. |
| Windows Forms 2.0 i nowsze wersje | W pełni obsługiwane. **Uwaga:**  Formanty NetFx są w pełni obsługiwane, ale nie wszystkie formanty innych firm są obsługiwane. |
| WPF 3.5 i nowsze wersje | W pełni obsługiwane.<br /><br /> **Uwaga** Formanty NetFx są w pełni obsługiwane, ale nie wszystkie formanty innych firm są obsługiwane. |
| Windows Win32 | Może pracować z niektórymi znanymi problemami, ale nie jest oficjalnie obsługiwany. |
| MFC | Obsługiwane częściowo. Zobacz [platformę UITest, aby](https://blogs.msdn.microsoft.com/vstsqualitytools/2010/04/15/uitest-framework-mfc-support-in-vs-2010/) uzyskać szczegółowe informacje o obsługiwanych funkcjach. |
| SharePoint | W pełni obsługiwane. |
| Aplikacje klienckie pakietu Office | Bez pomocy technicznej. |
| Klient sieci web Dynamics CRM | W pełni obsługiwane. |
| Klient Dynamics (Ax) 2012 | Akcje odtwarzania i nagrywania są obsługiwane częściowo. Zobacz [Visual Studio 10 kodowane interfejsu użytkownika / akcji nagrania obsługi microsoft dynamics,](https://blogs.msdn.microsoft.com/dave_froslie/2011/09/01/visual-studio-10-coded-ui-action-recordings-support-for-microsoft-dynamics-ax-2012/) aby uzyskać szczegółowe informacje. |
| SAP | Bez pomocy technicznej. |
| Citrix/usługi terminalowe | Nie zaleca się rejestrowania akcji na serwerze terminali. Rejestrator nie obsługuje uruchamiania wielu wystąpień w tym samym czasie. |
| PowerBuilder | Obsługiwane częściowo.<br /><br /> Obsługa zakresu ułatwień dostępu jest włączona dla formantów PowerBuilder. |

Aby uzyskać informacje dotyczące tworzenia rozszerzeń do obsługi innych platform, zobacz [Włączanie kodowanych testów interfejsu użytkownika formantów](../test/enable-coded-ui-testing-of-your-controls.md) i [rozszerzanie kodowanych testów interfejsu użytkownika i nagrań akcji](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md).

## <a name="see-also"></a>Zobacz też

- [Użyj automatyzacji interfejsu użytkownika, aby przetestować kod](../test/use-ui-automation-to-test-your-code.md)
