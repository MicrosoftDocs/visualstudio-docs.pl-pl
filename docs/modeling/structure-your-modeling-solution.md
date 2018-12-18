---
title: Tworzenie struktury rozwiązania modelowania
ms.date: 11/04/2016
ms.topic: conceptual
author: gewarren
ms.author: gewarren
manager: douge
ms.workload:
- multiple
ms.prod: visual-studio-dev15
ms.technology: vs-ide-modeling
ms.openlocfilehash: 2c279da9aed4a11799004a38004f8b82dca65174
ms.sourcegitcommit: 768d7877fe826737bafdac6c94c43ef70bf45076
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "50966716"
---
# <a name="structure-your-modeling-solution"></a>Tworzenie struktury rozwiązania modelowania

Aby skutecznie używać modeli w projekcie programistycznym, członkowie zespołu musi umożliwiać do pracy w modelach różnych części projektu, w tym samym czasie. W tym temacie sugeruje schemat podzielenie aplikacji na różne części, które odpowiadają warstw w ogólną diagram warstwowe.

Do uruchamiania w projekcie, lub szybko subproject, warto mieć szablon projektu, który następuje struktury projektu, który wybrano. W tym temacie opisano, jak utworzyć i używać tych szablonów.

W tym temacie założono, że pracujesz nad projektem, który jest wystarczająco duży, aby wymagać wielu członków zespołu, a być może jest kilka zespołów. Kod i modeli projektu są przechowywane w systemie kontroli źródła takie jak [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)]. Co najmniej niektórzy członkowie zespołu, użyj programu Visual Studio do tworzenia modeli i inni członkowie zespołu mogą wyświetlać te modele przy użyciu innych wersji programu Visual Studio.

Aby dowiedzieć się, które wersje programu Visual Studio obsługują każdej funkcji narzędzia i modelowanie, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="solution-structure"></a>Struktura rozwiązania

W średnich i dużych projektów strukturę zespołu opiera się na strukturę aplikacji. Każdy zespół korzysta z rozwiązania programu Visual Studio.

### <a name="to-divide-an-application-into-layers"></a>Aby podzielić na warstwy aplikacji

1. Podstawowa struktura rozwiązań struktury aplikacji, takie jak aplikacja sieci web, aplikacji usługi lub aplikacji pulpitu. Omówiono szereg typowych architektur w [Archetypes aplikacji w Przewodniku dotyczącym architektury aplikacji Microsoft](http://go.microsoft.com/fwlink/?LinkId=196681).

2. Tworzenie rozwiązań programu Visual Studio, którym Zadzwonimy rozwiązania architektury. To rozwiązanie będzie służyć do tworzenia ogólnego projektu systemu. Modele, ale żaden kod nie będzie zawierać.

   Dodaj diagram zależności do tego rozwiązania. Na diagramie zależności narysuj architektury który wybrano dla aplikacji. Na przykład diagram może wyświetlać te warstwy i zależności między nimi: prezentacji; Logika biznesowa; i dane.

4. Utwórz oddzielne rozwiązania Visual Studio dla każdej warstwy w diagram zależności architektury.

   Te rozwiązania będzie służyć do tworzenia kodu warstw.

5. Tworzenie modeli, które reprezentują wzorów, warstw i pojęcia, które są wspólne dla wszystkich warstw. Rozmieść modele, aby wszystkie modele są widoczne z rozwiązania architektury i modeli odpowiednie wynika z każdej warstwy.

   Można to osiągnąć przy użyciu jednej z poniższych procedur. Pierwszy alternatywna tworzy projekt modelowania osobne dla każdej warstwy, a druga tworzy projekt modelowania jednego, który jest udostępniany między warstwami.

#### <a name="use-a-separate-modeling-project-for-each-layer"></a>Użyj projektu modelowania osobne dla każdej warstwy

1. Utwórz projekt modelowania w rozwiązaniu do każdej warstwy.

   Ten model zawiera diagramy, które opisują wymagania i projektowania tej warstwy. Może również zawierać diagramów zależności, które pokazują zagnieżdżonych warstw.

   Istnieje już model dla każdej warstwy, a także modelu dla architektury aplikacji. Każdy model jest zawarty w własnego rozwiązania. Dzięki temu członkowie zespołu mogą pracować na warstwy, w tym samym czasie.

2. Do rozwiązania architektury Dodaj projekt modelowania poszczególnych rozwiązań warstwy. Aby to zrobić, otwórz rozwiązanie architektury. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł rozwiązania, wskaż polecenie Dodaj, a następnie kliknij przycisk **istniejący projekt**. Przejdź do projektu modelowania (.modelproj) w jednej warstwie rozwiązania.

   Każdy model jest teraz widoczne w dwóch rozwiązaniach: swoje rozwiązanie "domowy" i architektury rozwiązania.

3. Do każdej warstwy w projekcie modelowania dodać diagram zależności. Uruchom kopię diagram zależności architektury. Możesz usunąć elementy, które nie są zależności diagram zależności.

   Można również dodać diagramy zależności, które reprezentują szczegółowe strukturę tej warstwy.

   Te diagramy są używane do weryfikacji kodu utworzonego w tej warstwie.

4. W przypadku rozwiązania architektury edytować wymagania i modele projektu wszystkich warstw przy użyciu programu Visual Studio.

   W poszczególnych rozwiązaniach warstwy opracowywanie kodu dla tej warstwy, odnoszące się do modelu. Jeśli jesteś zawartości w celu opracowywania bez korzystania z tego samego komputera do aktualizacji modelu, można odczytania modelu i tworzenie kodu za pomocą wersji programu Visual Studio, której nie można tworzyć modele. Można również wygenerować kod z modelu w tych wersjach.

   Ta metoda gwarantuje, że nie zakłóceń jest spowodowana przez deweloperów, którzy edytowanie modeli warstw w tym samym czasie.

   Jednak ponieważ modele są oddzielone, jest trudne do odwoływania się do typowe pojęcia. Każdy model musi mieć własną kopię elementów, na których jest on zależny od innych warstw i architektury. Diagram zależności w każdej warstwie musi być synchronizowane z diagram zależności architektury. Jest trudne w utrzymaniu synchronizacji, gdy zmienią się te elementy, mimo że można tworzyć narzędzia, w tym celu.

#### <a name="use-a-separate-package-for-each-layer"></a>Użyj oddzielny pakiet dla każdej warstwy

1. W rozwiązaniu dla każdej warstwy Dodaj projekt modelowania architektury. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy węzeł rozwiązania, wskaż **Dodaj**, a następnie kliknij przycisk **istniejący projekt**. Projekt modelowania pojedynczego jest teraz dostępna z każdego rozwiązania: projekt architektury i projektu rozwoju dla każdej warstwy.

2. W modelu udostępnionego, należy utworzyć pakiet dla każdej warstwy: W **Eksploratora rozwiązań**, wybierz projekt modelowania. W **Eksploratora modelu UML**, kliknij prawym przyciskiem myszy węzeł główny modelu, wskaż **Dodaj**, a następnie kliknij przycisk **pakietu**.

   Każdy pakiet tak, będzie zawierać diagramy, które opisują wymagania i projektowania odpowiedniej warstwy.

3. W razie potrzeby należy dodać diagramów zależności lokalnych dla wewnętrznej struktury każdej warstwy.

   Ta metoda umożliwia elementy projektu każdej warstwy, aby odwoływać się bezpośrednio do tych warstw i popularną architekturę, od którego zależy.

   Równoczesną pracą na różnych pakietach mogą powodować konflikty, są one stosunkowo łatwe do zarządzania, ponieważ te pakiety są przechowywane w oddzielnych plikach.

## <a name="create-architecture-templates"></a>Tworzenie szablonów architektury

W praktyce nie należy tworzyć rozwiązania programu Visual Studio w tym samym czasie, ale dodaj je w miarę postępów projektu. Prawdopodobnie będziesz również użycie tej samej struktury rozwiązania w przyszłych projektów. Aby ułatwić szybkie tworzenie nowych rozwiązań, można utworzyć szablon rozwiązania lub projektu. Tak, aby łatwo Dystrybuuj i zainstalować na innych komputerach, można przechwycić szablonu w Visual Studio Integration rozszerzenie (VSIX).

Na przykład często używane rozwiązania mające warstwy prezentacji, biznesowych i danych, można skonfigurować szablon, który spowoduje utworzenie nowych rozwiązań, które mają tej struktury.

### <a name="to-create-a-solution-template"></a>Aby utworzyć szablon rozwiązania

1. [Pobierz i zainstaluj Kreatora eksportowania szablonu](http://go.microsoft.com/fwlink/?LinkId=196686).

2. Tworzenie struktury rozwiązania, którego chcesz użyć jako punktu wyjścia dla przyszłych projektów.

3. Na **pliku** menu, kliknij przycisk **Eksportuj szablon jako VSIX**.

   **Eksportuj szablon jako Kreator VSIX** zostanie otwarty.

4. Postępując zgodnie z instrukcjami w kreatorze Wybierz projekty, które chcesz uwzględnić w szablonie, podaj nazwę i opis szablonu i określanie lokalizacji wyjściowej.

## <a name="watch-a-video"></a>Obejrzyj film wideo

[Organizowanie modeli i zarządzania nimi](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-9-organizing-and-managing-your-models)

## <a name="see-also"></a>Zobacz też

- [Używanie modeli w procesie tworzenia aplikacji](../modeling/use-models-in-your-development-process.md)
- [Architektura Visual Studio — wskazówki dotyczące oprzyrządowania](../modeling/visual-studio-architecture-tooling-guidance.md)
