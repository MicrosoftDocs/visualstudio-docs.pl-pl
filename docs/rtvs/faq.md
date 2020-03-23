---
title: R Narzędzia dla programu Visual Studio często zadawane pytania
description: Często zadawane pytania dotyczące języka R w programie Visual Studio.
ms.date: 12/04/2017
ms.topic: reference
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 4eef8e79023bdd3bde03fec33c16a1c8f6d90446
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "72306263"
---
# <a name="frequently-asked-questions"></a>Często zadawane pytania

## <a name="visual-studio-support"></a>Pomoc techniczna programu Visual Studio

**P. Czy RTVS działa na OS X lub Linux?**

A. RTVS jest obecnie zbudowany na podstawie programu Visual Studio, który jest implementacją tylko dla systemu Windows. Firma Microsoft bada pomoc techniczną w programie Visual Studio Code i programie Visual Studio dla komputerów Mac. Zapoznaj się z [#1295 problemu RTVS](https://github.com/Microsoft/RTVS/issues/1295).

**P. Czy RTVS działa z wersjami Visual Studio Express?**

A. Nie.

**Pyt.: Czy można używać rozszerzeń programu Visual Studio z RTVS?**

A. Naturalnie. W rzeczywistości, oto kilka, które są popularne dla osób pracujących z R.

- [VsVim dla powiązań klawiszy vim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)
- [GitHub](https://marketplace.visualstudio.com/items?itemName=GitHub.GitHubExtensionforVisualStudio)
- [Edytor Markdown z podglądem na żywo](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.MarkdownEditor)

Więcej informacji można znaleźć w [portalu Visual Studio Marketplace.](https://marketplace.visualstudio.com/)

**P. Ponieważ RTVS jest w programie Visual Studio, czy oznacza to, że języka R można łatwo używać w języku C#, C++ i innych językach firmy Microsoft?**

A. Nie. RTVS jest narzędziem do tworzenia kodu R i używa standardowych natywnych interpreterów Języka R. Interop między R i innych języków nie jest obecnie obsługiwany.

**P. Czy RTVS działa z ustawieniami lokalnymi nieanglojęzycznymi?**

A. Wersja 1.0 RTVS jest dostępna tylko w języku angielskim. Wersja 1.1 zostanie zlokalizowana w tym samym zestawie języków, w których znajduje się sama wersja programu Visual Studio. W międzyczasie użyj [pakietu języka angielskiego dla programu Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=48157)lub programu Visual Studio 2017, uruchom instalatora i wybierz język angielski na karcie **Pakiety językowe.**

![Ustawienia międzynarodowe programu Visual Studio 2017](media/FAQ-international-settings.png)

**P. Bardzo podobają mi się moje bieżące ustawienia programu Visual Studio, ale chcę wypróbować nowe ustawienia nauki o danych. Co należy zrobić?**

A. Zapisz bieżące ustawienia programu Visual Studio przy użyciu**ustawień importu i eksportu** **narzędzi,** > a następnie przełącz się do ustawień nauki o danych. Aby przywrócić zapisane ustawienia, ponownie użyj polecenia **Zaimportuj i eksportuj ustawienia.**

**P. Czy mogę przechowywać projekt programu Visual Studio w udziale sieciowym?**

A. Nie, program Visual Studio nie obsługuje ładowania projektów z udziału sieciowego.

## <a name="r-interpretersintegration"></a>Tłumacze ustni R/integracja

**P. Z jakimi tłumaczami R współpracuje RTVS?**

A. [CRAN R](https://cran.r-project.org/), [Microsoft R Client i Microsoft Machine Learning Server](/machine-learning-server/)

**P. Gdzie mogę pobrać tych tłumaczy?**

A. Zobacz [Instalacja](installing-r-tools-for-visual-studio.md).

P **Co to jest serwer Microsoft R Server?**

A. R Server to dawna nazwa programu [Microsoft Machine Learning Server](/machine-learning-server/what-is-machine-learning-server).

**P. Czy RTVS współpracuje z 32-bitowymi wersjami R?**

A. Nie, RTVS obsługuje tylko 64-bitowe wersje R działające w 64-bitowych wersjach systemu Windows.

**P. Czy RTVS współpracuje z moim systemem kontroli źródła?**

A. Tak, można użyć dowolnego systemu kontroli źródła, który jest zintegrowany z programem Visual Studio.

**P. Jakie są zalecane ustawienia *.gitignore* dla projektu RTVS?**

A. GitHub prowadzi główne repozytorium zalecanych plików *.gitignore.* Możesz to zobaczyć tutaj: [R .gitignore](https://github.com/github/gitignore/blob/master/R.gitignore)

## <a name="remote-services"></a>Usługi zdalne

PYTANIE: **Co to są usługi zdalne w programie Visual Studio?**

A. Usługi zdalnego języka R dla programu Visual Studio umożliwiają skonfigurowanie komputera z systemem Windows lub Linux, a następnie połączenie z nim z rtvs. Zobacz [Konfigurowanie zdalnych obszarów roboczych](setting-up-remote-r-workspaces.md).

PYTANIE: **Czy RTVS może łączyć się z serwerem microsoft machine learning?**

A. Nie, ponieważ microsoft ML Server jest inną technologią i nie zapewnia tego samego mechanizmu łączności, co jest wymagane przez RTVS.

PYTANIE: **Czy RTVS można połączyć się z maszyną wirtualną utworzoną przy użyciu obrazu maszyny Wirtualnej nauki o danych na platformie Azure?**

A. Tak. obraz maszyny Wirtualnej nauki o danych — obraz [systemu Windows 2016](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/) jest fabrycznie zainstalowany z usługami zdalnego języka R dla programu Visual Studio.

P, **Czy RTVS może połączyć się z komputerem zdalnym z zainstalowanym r?**

Aby wykonać kod Języka R na komputerze zdalnym musi istnieć niektóre usługi nasłuchiwania żądań, odbieranie kodu i wysyłanie wyników z powrotem do komputera klienckiego. To jest to, co remote R Services for Visual Studio zrobić. Zobacz [Konfigurowanie zdalnych obszarów roboczych](setting-up-remote-r-workspaces.md).

PYTANIE: **Co to jest sesja zdalna?**

A. Zobacz artykuł [Wykonywanie na serwerze zdalnym](/machine-learning-server/r/how-to-execute-code-remotely) w dokumentacji serwera uczenia maszynowego.

## <a name="rtvs-development-and-features"></a>Rozwój i funkcje RTVS

**Q. Brak funkcji X, ale RStudio ma to!**

A. RStudio to fantastyczny i dojrzały IDE dla R, który jest w fazie rozwoju od wielu lat. RTVS stara się mieć wszystkie krytyczne funkcje, które są potrzebne, aby odnieść sukces. Pomóż ustalić priorytety przyszłych prac, zgłaszając problemy w [serwisie GitHub](https://github.com/Microsoft/RTVS/issues/).

**P. Czy mogę przyczynić się do RTVS?**

A. Jak najbardziej! Kod źródłowy mieszka na [Github](https://github.com/microsoft/RTVS). Użyj śledzenia problemów, aby przesłać błędy i skomentować te, które zostały już złożone.

Możesz również dodać do tej&mdash;dokumentacji po prostu wybierz polecenie **Edytuj** w prawym górnym rogu dowolnej strony. Komentarze do dokumentów są również mile widziane, które można dodać na dole dowolnej strony.
