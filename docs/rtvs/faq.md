---
title: Narzędzia języka R dla programu Visual Studio — często zadawane pytania
description: Często zadawane pytania w języku R w programie Visual Studio.
ms.date: 12/04/2017
ms.prod: visual-studio-dev15
ms.technology: vs-rtvs
ms.topic: reference
author: kraigb
ms.author: kraigb
manager: douge
ms.workload:
- data-science
ms.openlocfilehash: 29634d63cf8e898203ff4d72a23296bdb14019e0
ms.sourcegitcommit: 75e02ed88a1ace6e8265fd4e3a82a1bc78f3adca
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/13/2018
ms.locfileid: "53348481"
---
# <a name="frequently-asked-questions"></a>Często zadawane pytania

## <a name="visual-studio-support"></a>Pomoc techniczna dla programu Visual Studio

**PYTANIA I ODPOWIEDZI. RTVS działa systemie OS X lub Linux?**

A. RTVS obecnie bazuje na usłudze Visual Studio, który jest wdrożenie oparte tylko na Windows. Firma Microsoft analizuje pomocy technicznej w programie Visual Studio Code i Visual Studio dla komputerów Mac. Zapoznaj się [RTVS wystawiać #1295](https://github.com/Microsoft/RTVS/issues/1295).

**PYTANIA I ODPOWIEDZI. RTVS działa z wersjami programu Visual Studio Express?**

A. Nie.

**PYTANIA I ODPOWIEDZI. Czy można użyć rozszerzeń programu Visual Studio za pomocą RTVS?**

A. Oczywiście. W rzeczywistości Oto kilka, które są popularne dla osób pracujących z językiem R.

- [VsVim dla vim powiązań klawiszy](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)
- [GitHub](https://marketplace.visualstudio.com/items?itemName=GitHub.GitHubExtensionforVisualStudio)
- [Edytor języka znaczników markdown za pomocą podglądu na żywo](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.MarkdownEditor)

Zobacz [Visual Studio Marketplace](https://marketplace.visualstudio.com/) Aby dowiedzieć się więcej.

**PYTANIA I ODPOWIEDZI. Ponieważ RTVS znajduje się w programie Visual Studio, to znaczy, że języka R mogą być łatwo używane z C#, C++ i inne języki firmy Microsoft?**

A. Nie. RTVS jest narzędziem do tworzenia kodu języka R i używa standardowych natywnych interpreterów języka R. Współdziałanie języków R i innych języków nie jest obecnie obsługiwane.

**PYTANIA I ODPOWIEDZI. RTVS działa przy użyciu ustawień regionalnych innych niż angielski?**

A. Wersja 1.0 RTVS jest tylko do języka angielskiego. W wersji 1.1 zostanie zlokalizowany dla tego samego zestawu języków, które jest programu Visual Studio. W międzyczasie użyj [pakiet językowy dla programu Visual Studio 2015 w języku angielskim](https://www.microsoft.com/download/details.aspx?id=48157), lub w programie Visual Studio 2017, uruchom Instalatora i wybierz w języku angielskim w **pakiety językowe** kartę.

![Ustawienia międzynarodowe w programie Visual Studio 2017](media/FAQ-international-settings.png)

**PYTANIA I ODPOWIEDZI. Podoba mi się naprawdę Moje bieżące ustawienia programu Visual Studio, ale chcę, aby wypróbować nowe ustawienia do nauki o danych. Co należy zrobić?**

A. Zapisać bieżące ustawienia programu Visual Studio przy użyciu **narzędzia** > **Import i eksport ustawień**, następnie przejdź do ustawień do nauki o danych. Aby przywrócić zapisane ustawienia, należy użyć **Import i eksport ustawień** ponownie polecenie.

**PYTANIA I ODPOWIEDZI. W sieciowym udziale można przechowywać mój projekt programu Visual Studio?**

A. Nie, program Visual Studio nie obsługuje ładowania projektów z udziału sieciowego.

## <a name="r-interpretersintegration"></a>Integracja interpreterów języka R

**PYTANIA I ODPOWIEDZI. Jakie interpreterów języka R RTVS działa z?**

A. [CRAN R](https://cran.r-project.org/), [Microsoft R Client i Microsoft Machine Learning Server](/machine-learning-server/)

**PYTANIA I ODPOWIEDZI. Gdzie można pobrać te interpretery?**

A. Zobacz [instalacji](installing-r-tools-for-visual-studio.md).

Q **co to jest Microsoft R Server?**

A. R Server to poprzednia nazwa [serwer Microsoft Machine Learning](/machine-learning-server/what-is-machine-learning-server).

**PYTANIA I ODPOWIEDZI. Czy RTVS współpracuje z 32-bitowe wersje języka r?**

A. Nie, RTVS obsługuje tylko 64-bitowe wersje języka r z systemem 64-bitowe wersje systemu Windows.

**PYTANIA I ODPOWIEDZI. RTVS działa z moim systemem kontroli źródła?**

A. Tak, można użyć do systemu kontroli źródła, która jest zintegrowana w programie Visual Studio.

**PYTANIA I ODPOWIEDZI. Co to są zalecanym *.gitignore* ustawienia dla projektu RTVS?**

A. Serwis GitHub zachowuje głównego repozytorium zalecane *.gitignore* plików. Być może ją opublikujemy: [R .gitignore](https://github.com/github/gitignore/blob/master/R.gitignore)

## <a name="remote-services"></a>Usługi zdalnej

PYTANIE: **Co to jest usługi zdalnej w programie Visual Studio?**

A. Remote R Services dla programu Visual Studio pozwala na skonfigurowanie komputera Windows lub Linux, a następnie połączyć je z RTVS. Zobacz [Konfigurowanie zdalnych obszarów roboczych](setting-up-remote-r-workspaces.md).

PYTANIE: **Czy RTVS się połączyć serwer Microsoft Machine Learning?**

A. Nie, ponieważ Microsoft ML Server jest różne technologie i nie zapewnia ten sam mechanizm łączności jako wymagane przez RTVS.

PYTANIE: **Można RTVS łączyć się z maszyny Wirtualnej utworzonej przy użyciu obrazu maszyny Wirtualnej do nauki o danych na platformie Azure?**

A. Tak; [maszyna wirtualna z analizy danych — Windows 2016](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/) obraz jest dostarczany z preinstalowanym systemem Remote R Services dla programu Visual Studio.

Pytania i odpowiedzi, **RTVS może nawiązać połączenie z komputera zdalnego z zainstalowanym językiem r.?**

Aby wykonać kod R na komputerze zdalnym, musi istnieć pewne service nasłuchiwania żądań, kod odbieranie i wysyłanie wyników z powrotem do komputera klienckiego. Jest to, czego Remote R Services dla programu Visual Studio. Zobacz [Konfigurowanie zdalnych obszarów roboczych](setting-up-remote-r-workspaces.md).

PYTANIE: **Co to jest sesja zdalna?**

A. Zapoznaj się z artykułem [wykonaj na serwerze zdalnym](/machine-learning-server/r/how-to-execute-code-remotely) w dokumentacji serwer Machine Learning.

## <a name="rtvs-development-and-features"></a>Programowanie RTVS i funkcje

**PYTANIA I ODPOWIEDZI. Brak dotycząca funkcji X, ale RStudio zostało ono!**

A. Program RStudio jest Niesamowity i dojrzała środowisko IDE dla języka R, które było opracowywane przez wiele lat. RTVS stara się o wszystkich funkcji krytycznych, wymagających zakończy się powodzeniem. Pomagają określić priorytety przyszłych zadań, wykonując [ankiety RTVS](https://www.surveymonkey.com/r/RTVS1) i problemy dotyczące plików w [GitHub](https://github.com/Microsoft/RTVS/issues/).

**PYTANIA I ODPOWIEDZI. Czy mogę współtworzyć RTVS?**

A. Jak najbardziej! Kod źródłowy znajduje się w witrynie [Github](https://github.com/microsoft/RTVS). Narzędzie do śledzenia problemów umożliwia zgłaszanie błędów i komentarze dotyczące tych już zgłoszone.

Zachęcamy do współtworzenia tej dokumentacji&mdash;po prostu wybierz opcję **Edytuj** polecenia w prawym górnym rogu każdej strony. Komentarze dotyczące dokumentów są również Zapraszamy, które można dodać u dołu każdej strony.
