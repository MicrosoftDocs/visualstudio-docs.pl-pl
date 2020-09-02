---
title: R Tools for Visual Studio często zadawane pytania
description: Często zadawane pytania dotyczące języka R w programie Visual Studio.
ms.date: 12/04/2017
ms.topic: reference
author: kraigb
ms.author: kraigb
manager: jillfra
ms.workload:
- data-science
ms.openlocfilehash: 8c89f1d59405fb7475e827cac9624c6623d7041e
ms.sourcegitcommit: 1d74273a50ede5a90d9d64372d93aad357daef42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "89365668"
---
# <a name="frequently-asked-questions"></a>Często zadawane pytania

## <a name="visual-studio-support"></a>Obsługa programu Visual Studio

**Pytania. Czy RTVS działa w systemie OS X lub Linux?**

A. RTVS jest obecnie oparta na programie Visual Studio, który jest implementacją tylko dla systemu Windows. Firma Microsoft bada pomoc techniczną dotyczącą Visual Studio Code i Visual Studio dla komputerów Mac. Zapoznaj się z tematem [#1295 problemu RTVS](https://github.com/Microsoft/RTVS/issues/1295).

**Pytania. Czy RTVS współpracuje z wersjami Visual Studio Express?**

A. Nie.

**Pytania. Czy mogę używać rozszerzeń programu Visual Studio z programem RTVS?**

A. Oczywiście. Oto kilka popularnych, które są popularne dla osób pracujących w języku R.

- [VsVim dla powiązań kluczy vim](https://marketplace.visualstudio.com/items?itemName=JaredParMSFT.VsVim)
- [GitHub](https://marketplace.visualstudio.com/items?itemName=GitHub.GitHubExtensionforVisualStudio)
- [Edytor promocji z podglądem na żywo](https://marketplace.visualstudio.com/items?itemName=MadsKristensen.MarkdownEditor)

Zobacz [Visual Studio Marketplace](https://marketplace.visualstudio.com/) , aby uzyskać więcej informacji.

**Pytania. Ponieważ RTVS jest w programie Visual Studio, oznacza to, że język R może być łatwo używany w języku C#, C++ i innych językach firmy Microsoft?**

A. Nie. RTVS to narzędzie do tworzenia kodu języka R i używa standardowych natywnych interpreterów języka R. Współdziałanie między językami R i innymi nie jest obecnie obsługiwane.

**Pytania. Czy RTVS współpracuje z ustawieniami regionalnymi innymi niż angielski?**

A. Wersja 1,0 RTVS jest tylko w języku angielskim. Wersja 1,1 będzie lokalizowana do tego samego zestawu języków, który sam program Visual Studio. W międzyczasie Użyj [pakietu języka angielskiego dla programu Visual studio 2015](https://www.microsoft.com/download/details.aspx?id=48157)lub w programie visual Studio 2017, uruchom Instalatora i wybierz pozycję angielski na karcie **pakiety językowe** .

![Ustawienia międzynarodowe dla programu Visual Studio 2017](media/FAQ-international-settings.png)

**Pytania. Podoba mi się Moje bieżące ustawienia programu Visual Studio, ale chcę wypróbować nowe ustawienia analizy danych. Co mam zrobić?**

A. Zapisz bieżące ustawienia programu Visual **Studio za pomocą opcji**  >  **Importuj i Eksportuj ustawienia**, a następnie przejdź do ustawień analizy danych. Aby przywrócić zapisane ustawienia, użyj polecenia **Importuj i Eksportuj ustawienia** ponownie.

**Pytania. Czy mogę przechowywać projekt programu Visual Studio w udziale sieciowym?**

A. Nie, program Visual Studio nie obsługuje ładowania projektów z udziału sieciowego.

## <a name="r-interpretersintegration"></a>Interpretery języka R/integracja

**Pytania. Z jakich interpreterów języka R RTVS współpracuje?**

A. [Cran R](https://cran.r-project.org/), [Microsoft R Client i Microsoft Machine Learning Server](/machine-learning-server/)

**Pytania. Gdzie mogę pobrać te interpretery?**

A. Zobacz [Instalacja](installing-r-tools-for-visual-studio.md).

**Co to jest Microsoft R Server?**

A. R Server jest wcześniejszą nazwą [Microsoft Machine Learning Server](/machine-learning-server/what-is-machine-learning-server).

**Pytania. Czy RTVS współpracuje z 32-bitowymi wersjami języka R?**

A. Nie, RTVS obsługuje tylko 64-bitowe wersje języka R działające w 64-bitowych wersjach systemu Windows.

**Pytania. Czy RTVS współpracuje z systemem kontroli źródła?**

A. Tak, można użyć dowolnego systemu kontroli źródła zintegrowanego z Visual Studio.

**Pytania. Jakie są zalecane ustawienia *GITIGNORE* dla projektu RTVS?**

A. Usługi GitHub przechowują repozytorium zalecanych plików *. gitignore* . Zobaczysz to tutaj: [R. gitignore](https://github.com/github/gitignore/blob/master/R.gitignore)

## <a name="remote-services"></a>Usługi zdalne

PYTANIE: **Co to są usługi zdalne w programie Visual Studio?**

A. Usługa Remote R Services dla programu Visual Studio umożliwia skonfigurowanie komputera z systemem Windows lub Linux, a następnie nawiązanie z nim połączenia z RTVS. Zobacz [Konfigurowanie zdalnych obszarów roboczych](setting-up-remote-r-workspaces.md).

PYTANIE: **Czy RTVS połączyć się z Microsoft Machine Learning Server?**

A. Nie, ponieważ program Microsoft ML Server jest inną technologią i nie zapewnia tego samego mechanizmu łączności, zgodnie z wymaganiami RTVS.

PYTANIE: **Czy RTVS można nawiązać połączenie z maszyną wirtualną utworzoną przy użyciu obrazu Data Science VM na platformie Azure?**

A. Opcję obraz [Data Science VM-Windows 2016](https://azure.microsoft.com/services/virtual-machines/data-science-virtual-machines/) jest preinstalowany ze zdalnymi usługami R Services dla programu Visual Studio.

P **może RTVS nawiązać połączenie z maszyną zdalną z zainstalowanym programem R?**

Aby wykonać kod R na maszynie zdalnej, musi istnieć pewna usługa, która nasłuchuje żądań, odbiera kod i wysyła wyniki z powrotem do komputera klienckiego. Jest to usługa Remote R Services dla programu Visual Studio. Zobacz [Konfigurowanie zdalnych obszarów roboczych](setting-up-remote-r-workspaces.md).

PYTANIE: **Co to jest Sesja zdalna?**

A. Zapoznaj się z artykułem [wykonywanie na serwerze zdalnym](/machine-learning-server/r/how-to-execute-code-remotely) w dokumentacji Machine Learning Server.

## <a name="rtvs-development-and-features"></a>RTVS programowanie i funkcje

**Brak funkcji Q. feature X, ale RStudio ma!**

A. RStudio to fantastycznie i dojrzałe środowisko IDE dla języka R, które jest opracowywane przez wiele lat. RTVS szuka wszystkich kluczowych funkcji, które należy wykonać, aby zakończyć się pomyślnie. Pomóż w ustalaniu priorytetów w przyszłości dzięki wykorzystaniu problemów w serwisie [GitHub](https://github.com/Microsoft/RTVS/issues/).

**Pytania. Czy mogę współtworzyć RTVS?**

A. Jak najbardziej! Kod źródłowy jest w serwisie [GitHub](https://github.com/microsoft/RTVS). Użyj narzędzia do śledzenia problemów, aby przesłać usterki i komentarz dotyczący już zgłoszonych.

Zapraszamy również do współtworzenia tej dokumentacji &mdash; po prostu wybierz polecenie **Edytuj** w prawym górnym rogu dowolnej strony. Komentarze w dokumentacji są również Zapraszamy, którą można dodać u dołu dowolnej strony.
