---
title: Konfiguracje i platformy dla kodowanych testów interfejsu użytkownika
description: Ten artykuł zawiera obsługiwane konfiguracje i platformy dla kodowanych testów interfejsu użytkownika dla Visual Studio Enterprise.
ms.custom: SEO-VS-2020
ms.date: 10/04/2015
ms.topic: reference
helpviewer_keywords:
- coded UI tests
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
author: mikejo5000
ms.openlocfilehash: 2b749375c398b3deb6ac56e8b1a787b0bcb82b22
ms.sourcegitcommit: 9ce13a961719afbb389fa033fbb1a93bea814aae
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/30/2020
ms.locfileid: "96330254"
---
# <a name="supported-configurations-and-platforms-for-coded-ui-tests-and-action-recordings"></a>Obsługiwane konfiguracje i platformy dla kodowanych testów interfejsu użytkownika i nagrań akcji

Obsługiwane konfiguracje i platformy dla kodowanych testów interfejsu użytkownika dla Visual Studio Enterprise są wymienione w poniższej tabeli. Te konfiguracje mają zastosowanie również do nagrań akcji utworzonych przy użyciu programu [!INCLUDE[MTRlong](../test/includes/mtrlong_md.md)] .

> [!NOTE]
> Proces kodowanego testu interfejsu użytkownika musi mieć takie same uprawnienia, jak aplikacja poddawana testom.

[!INCLUDE [coded-ui-test-deprecation](includes/coded-ui-test-deprecation.md)]

**Wymagania**

- Visual Studio Enterprise

## <a name="supported-configurations"></a>Obsługiwane konfiguracje

| Konfiguracja | Obsługiwane |
|-| - |
| Systemy operacyjne | [!INCLUDE[win7](../debugger/includes/win7_md.md)]<br /><br /> [!INCLUDE[winsvr08_r2](../debugger/includes/winsvr08_r2_md.md)]<br /><br /> [!INCLUDE[win8](../debugger/includes/win8_md.md)]<br /><br /> Windows 10 |
| Obsługa wersji 32-/64-bitowej | 32-bitowy system Windows z systemem 32-bitowym [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] może testować aplikacje 32-bitowe.<br /><br /> 64 — bit systemu Windows z systemem 32-bitowym [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] może testować 32-bitowe aplikacje Wow z interfejsem użytkownika Synchronization. n.<br /><br /> 64-bitowy system Windows z systemem 32-bitowym [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] może testować 64-bitowe Windows Forms i aplikacje WPF, które nie mają synchronizacji interfejsu użytkownika. |
| Architektura | w przypadku procesorów x86 i x64 **:**  program Internet Explorer nie jest obsługiwany w trybie 64-bitowym, z wyjątkiem sytuacji, gdy jest uruchomiony w [!INCLUDE[win8](../debugger/includes/win8_md.md)] wersji lub nowszej. |
| .NET | .NET 2.0, 3.0, 3.5, 4 i 4.5. **Uwaga:** [!INCLUDE[TCMext](../misc/includes/tcmext_md.md)] Program Visual Studio będzie wymagał działania programu .NET 4.   Jednak aplikacje opracowane za pomocą wymienionych wersji środowiska .NET są obsługiwane. |

> [!NOTE]
> *Synchronizacja interfejsu użytkownika* to funkcja, w której odtwarzanie jest weryfikowane w kolejce wiadomości każdej kontrolki. Jeśli formant nie odpowiedział na zdarzenie, które zostało do niego wysłane, zdarzenie jest wysyłane ponownie.

## <a name="platform-support"></a>Obsługa platform

| Platforma | Poziom wsparcia |
|-| - |
| Aplikacje Windows Phone | Obsługiwane są tylko aplikacje dla telefonów opartych na języku WinRT-XAML. |
| Aplikacje platformy UWP | Obsługiwane są tylko aplikacje platformy UWP oparte na języku XAML. |
| Aplikacje uniwersalne systemu Windows | Obsługiwane są tylko aplikacje uniwersalne systemu Windows oparte na języku XAML na telefonie i pulpicie. |
| Edge | Rejestrowanie kroków akcji lub użycie konstruktora do wyświetlania właściwości obiektu nie jest obsługiwane. Testy mogą być odtwarzane w przeglądarce Edge przy użyciu programu Visual Studio 2015 Update 2 i nowszych wersji za pomocą [rozszerzenia kodowanego przetestowania między przeglądarkami interfejsu użytkownika](https://marketplace.visualstudio.com/items?itemName=AtinBansal.SeleniumcomponentsforCodedUICrossBrowserTesting). |
| Internet Explorer 8<br /><br /> Internet Explorer 9<br /><br /> Ważne w programie Internet Explorer 10 **:**  program Internet Explorer 10 jest obsługiwany tylko na pulpicie. <br /><br /> Internet Explorer 11 **Ważne:**  program Internet Explorer 11 jest obsługiwany tylko na pulpicie. | W pełni obsługiwane.<br /><br /> -   **Obsługa języka HTML5 w programie Internet Explorer 9 i Internet Explorer 10:** Kodowane testy interfejsu użytkownika obsługują rejestrowanie, odtwarzanie i sprawdzanie poprawności formantów HTML5: audio, wideo, ProgressBar i Slider. Aby uzyskać więcej informacji, zobacz [Korzystanie z kontrolek HTML5 w kodowanych testach interfejsu użytkownika](../test/using-html5-controls-in-coded-ui-tests.md). **Ostrzeżenie:**      Jeśli utworzysz kodowane testy interfejsu użytkownika w programie Internet Explorer 10, mogą one nie działać w programie Internet Explorer 9 lub Internet Explorer 8. Jest to spowodowane tym, że Internet Explorer 10 zawiera formanty HTML5, takie jak audio, wideo, pasek postępu i suwak. Te formanty HTML5 nie są rozpoznawane przez Internet Explorer 9 i Internet Explorer 8. Podobnie test interfejsu użytkownika kodowany za pomocą Internet Explorer 9 może zawierać niektóre formanty języka HTML5, które również nie zostaną rozpoznane przez Internet Explorer 8.<br />-   **Obsługa sprawdzania pisowni w programie Internet Explorer 10:** Program Internet Explorer 10 obejmuje możliwości sprawdzania pisowni dla wszystkich pól tekstowych. Pozwala to na wybranie z listy sugerowanych poprawek. Kodowany test interfejsu użytkownika będzie ignorować czynności użytkownika, takie jak zaznaczenie sugestii alternatywnej pisowni. Rejestrowany będzie tylko końcowy tekst wpisany w polu tekstowym.<br />     Następujące akcje są rejestrowane dla kodowanych testów interfejsu użytkownika, które używają formantu sprawdzania pisowni: Dodaj do słownika, Kopiuj, Zaznacz wszystko, Dodaj do słownika i Ignoruj.<br />-   **Obsługa 64-bitowego programu Internet Explorer działającego w systemie Windows 8:** Wcześniej 64-bitowe wersje programu Internet Explorer nie były obsługiwane dla nagrywania i odtwarzania. W przypadku [!INCLUDE[win8](../debugger/includes/win8_md.md)] i [!INCLUDE[vs_dev11_long](../data-tools/includes/vs_dev11_long_md.md)] , kodowane testy interfejsu użytkownika zostały włączone dla 64-bitowych wersji programu Internet Explorer. **Ostrzeżenie:**      64-bitowe wsparcie dla programu Internet Explorer ma zastosowanie tylko wtedy, gdy jest uruchomiony program [!INCLUDE[win8](../debugger/includes/win8_md.md)] lub nowszy.<br />-   **Obsługa przypiętych witryn w programie Internet Explorer 9:** W programie Internet Explorer 9 wprowadzono przypięte witryny. Dzięki przypiętym witrynom można przejść do ulubionych witryn bezpośrednio z paska zadań systemu Windows — bez konieczności wcześniejszego otwierania Internet Explorer. Kodowane testy interfejsu użytkownika mogą teraz świadomie generować akcje na przypiętych witrynach. Aby uzyskać więcej informacji na temat przypiętych witryn, zobacz [przypięte witryny](https://support.microsoft.com/hub/4230784/internet-explorer-help).<br />-   **Obsługa tagów semantycznych programu Internet Explorer 9:** W programie Internet Explorer 9 wprowadzono następujące znaczniki semantyczne: sekcja, NAV, artykuł, odłogowanie, hgroup, nagłówek, stopka, rysunek, figcaption i Mark. Kodowane testy interfejsu użytkownika ignorują wszystkie te znaczniki semantyczne podczas nagrywania. Możesz dodać potwierdzenia na tych tagach za pomocą Konstruktora kodowanego testu interfejsu użytkownika. Można użyć pokrętła nawigacji w Konstruktorze kodowanego testu interfejsu użytkownika, aby nawigować do jednego z tych elementów i przeglądać ich właściwości.<br />-   **Bezproblemowe obsługiwanie białych znaków między wersjami programu Internet Explorer:** Istnieją różnice między obsługą białych znaków w programie Internet Explorer 8, Internet Explorer 9 i Internet Explorer 10. Kodowany test interfejsu użytkownika bezproblemowo obsługuje te różnice. Dlatego kodowany test interfejsu użytkownika, utworzony na przykład w Internet Explorer 8, będzie z powodzeniem odtwarzany w Internet Explorer 9 i Internet Explorer 10.<br />-   **W obszarze powiadomień programu Internet Explorer są teraz rejestrowane z ustawionym zestawem atrybutów "Kontynuuj po błędzie":** Wszystkie akcje w obszarze powiadomień programu Internet Explorer są teraz rejestrowane z ustawionym zestawem atrybutów "Kontynuuj po błędzie". Jeśli nie ma paska powiadomień podczas odtwarzania, operacje na nim zostaną zignorowane i kodowany test interfejsu użytkownika przejdzie do następnej akcji. |
| Formanty Windows Forms i WPF innych firm | W pełni obsługiwane.<br /><br /> Aby włączyć formanty innych firm w formularzach Windows Forms i aplikacjach WPF, należy dodać odwołania i kod. Aby uzyskać więcej informacji, zobacz [Włączanie testowania kodowanego interfejsu użytkownika dla kontrolek](../test/enable-coded-ui-testing-of-your-controls.md). |
| Internet Explorer 6<br /><br /> Internet Explorer 7 | Nieobsługiwane. |
| Chrome<br /><br /> Firefox | Rejestrowanie czynności nie jest obsługiwane. Zakodowane testy interfejsu użytkownika mogą być odtwarzane w przeglądarkach Chrome i Firefox z programu Visual Studio 2012 aktualizacja 4 lub nowsza. Przejdź [tutaj](using-different-web-browsers-with-coded-ui-tests.md) , aby uzyskać więcej szczegółów. |
| Opera<br /><br /> Safari | Nieobsługiwane. |
| Silverlight | Nieobsługiwane.<br /><br /> W przypadku programu Visual Studo 2013 można jednak pobrać [wtyczkę kodowanego testu interfejsu użytkownika Microsoft Visual Studio 2013 dla programu Silverlight](https://marketplace.visualstudio.com/items?itemName=PrachiBoraMSFT.MicrosoftVisualStudio2013CodedUITestPluginforSilve) z galerii programu Visual Studio. |
| Flash/Java | Nieobsługiwane. |
| Windows Forms 2.0 i nowsze wersje | W pełni obsługiwane. **Uwaga:**  Formanty NetFx są w pełni obsługiwane, ale nie wszystkie formanty innych firm są obsługiwane. |
| WPF 3.5 i nowsze wersje | W pełni obsługiwane.<br /><br /> **Uwaga** Formanty NetFx są w pełni obsługiwane, ale nie wszystkie formanty innych firm są obsługiwane. |
| Windows Win32 | Może pracować z niektórymi znanymi problemami, ale nie jest oficjalnie obsługiwany. |
| MFC | Obsługiwane częściowo. Zobacz [UITest Framework](/archive/blogs/vstsqualitytools/uitest-framework-mfc-support-in-vs-2010) , aby uzyskać szczegółowe informacje o obsługiwanych funkcjach. |
| SharePoint | W pełni obsługiwane. |
| Aplikacje klienckie pakietu Office | Nieobsługiwane. |
| Klient sieci web Dynamics CRM | W pełni obsługiwane. |
| Klient Dynamics (Ax) 2012 | Akcje odtwarzania i nagrywania są obsługiwane częściowo. Aby uzyskać szczegółowe informacje, zobacz Program [Visual Studio 10 kodowanego interfejsu użytkownika i obsługi nagrań akcji dla systemu Microsoft Dynamics](/archive/blogs/dave_froslie/visual-studio-10-coded-ui-action-recordings-support-for-microsoft-dynamics-ax-2012) . |
| SAP | Nieobsługiwane. |
| Citrix/usługi terminalowe | Nie zalecamy rejestrowania akcji na serwerze terminali. Rejestrator nie obsługuje jednoczesnego uruchamiania wielu wystąpień. |
| PowerBuilder | Obsługiwane częściowo.<br /><br /> Obsługa zakresu ułatwień dostępu jest włączona dla formantów PowerBuilder. |

Aby uzyskać informacje na temat sposobu tworzenia rozszerzeń do obsługi innych platform, zobacz [Włączanie testowania kodowanego interfejsu użytkownika dla kontrolek](../test/enable-coded-ui-testing-of-your-controls.md) i [rozszerzanie KODOWANYCH testów interfejsu użytkownika i nagrań akcji](../test/extending-coded-ui-tests-and-action-recordings-to-support-microsoft-excel.md).

## <a name="see-also"></a>Zobacz też

- [Używanie automatyzacji interfejsu użytkownika do testowania kodu](../test/use-ui-automation-to-test-your-code.md)