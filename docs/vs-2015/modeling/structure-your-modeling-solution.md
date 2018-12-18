---
title: Tworzenie struktury rozwiązania modelowania | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-tfs-dev14
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2ba70ba4-2cea-4e01-93c2-055903d59470
caps.latest.revision: 16
author: gewarren
ms.author: gewarren
manager: douge
ms.openlocfilehash: 995192b372b9c1909ad3a7f164474cfaf63f07bc
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51784458"
---
# <a name="structure-your-modeling-solution"></a>Tworzenie struktury rozwiązania modelowania
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby skutecznie używać modeli w projekcie programistycznym, członkowie zespołu musi umożliwiać do pracy w modelach różnych części projektu, w tym samym czasie. W tym temacie sugeruje schemat podzielenie aplikacji na różne części, które odpowiadają warstw w ogólną diagram warstwowe.  
  
 Do uruchamiania w projekcie, lub szybko subproject, warto mieć szablon projektu, który następuje struktury projektu, który wybrano. W tym temacie opisano, jak utworzyć i używać tych szablonów.  
  
 W tym temacie założono, że pracujesz nad projektem, który jest wystarczająco duży, aby wymagać wielu członków zespołu, a być może jest kilka zespołów. Kod i modeli projektu są przechowywane w systemie kontroli źródła takie jak [!INCLUDE[esprtfs](../includes/esprtfs-md.md)]. Co najmniej niektórzy członkowie zespołu, użyj programu Visual Studio do tworzenia modeli i inni członkowie zespołu mogą wyświetlać te modele przy użyciu innych wersji programu Visual Studio.  
  
 Aby dowiedzieć się, które wersje programu Visual Studio obsługują każdej funkcji narzędzia i modelowanie, zobacz [obsługiwana wersja dla narzędzia architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).  
  
## <a name="solution-structure"></a>Struktura rozwiązania  
 W średnich i dużych projektów strukturę zespołu opiera się na strukturę aplikacji. Każdy zespół korzysta z rozwiązania programu Visual Studio.  
  
#### <a name="to-divide-an-application-into-layers"></a>Aby podzielić na warstwy aplikacji  
  
1. Podstawowa struktura rozwiązań struktury aplikacji, takie jak aplikacja sieci web, aplikacji usługi lub aplikacji pulpitu. Omówiono szereg typowych architektur w [Archetypes aplikacji w Przewodniku dotyczącym architektury aplikacji Microsoft](http://go.microsoft.com/fwlink/?LinkId=196681).  
  
2. Utwórz [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] rozwiązania, które firma Microsoft będzie wywoływać rozwiązania architektury. To rozwiązanie będzie służyć do tworzenia ogólnego projektu systemu. Modele, ale żaden kod nie będzie zawierać.  
  
    Dodaj diagram warstwowy do tego rozwiązania. Na diagramie warstwowym narysuj architektury który wybrano dla aplikacji. Na przykład diagram może wyświetlać te warstwy i zależności między nimi: prezentacji; Logika biznesowa; i dane.  
  
    W tym samym czasie można utworzyć diagram warstwy i nowego rozwiązania programu Visual Studio przy użyciu **nowe UML lub diagramu warstwowego** polecenie **architektury** menu.  
  
3. Dodawanie do diagramów UML model architektury, które reprezentują koncepcji biznesowych ważne i zastosowań, które są określane w projekcie wszystkie warstwy.  
  
4. Utwórz oddzielne rozwiązania Visual Studio dla każdej warstwy na diagramie warstwy architektury.  
  
    Te rozwiązania będzie służyć do tworzenia kodu warstw.  
  
5. Tworzenie modeli UML, reprezentujących wzorów, warstw i pojęcia, które są wspólne dla wszystkich warstw. Rozmieść modele, aby wszystkie modele są widoczne z rozwiązania architektury i modeli odpowiednie wynika z każdej warstwy.  
  
    Można to osiągnąć przy użyciu jednej z poniższych procedur. Pierwszy alternatywna tworzy projekt modelowania osobne dla każdej warstwy, a druga tworzy projekt modelowania jednego, który jest udostępniany między warstwami.  
  
   ###### <a name="to-use-a-separate-modeling-project-for-each-layer"></a>Aby użyć projektu modelowania osobne dla każdej warstwy  
  
   1. Utwórz projekt modelowania w rozwiązaniu do każdej warstwy.  
  
       Ten model zawiera diagramy UML, zawierających opis wymagań i projektowania tej warstwy. Może również zawierać diagramy warstwowe, które pokazują zagnieżdżonych warstw.  
  
       Istnieje już model dla każdej warstwy, a także modelu dla architektury aplikacji. Każdy model jest zawarty w własnego rozwiązania. Dzięki temu członkowie zespołu mogą pracować na warstwy, w tym samym czasie.  
  
   2. Do rozwiązania architektury Dodaj projekt modelowania poszczególnych rozwiązań warstwy. Aby to zrobić, otwórz rozwiązanie architektury. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy węzeł rozwiązania, wskaż polecenie Dodaj, a następnie kliknij **istniejący projekt**. Przejdź do projektu modelowania (.modelproj) w jednej warstwie rozwiązania.  
  
       Każdy model jest teraz widoczne w dwóch rozwiązaniach: swoje rozwiązanie "domowy" i architektury rozwiązania.  
  
   3. Do każdej warstwy w projekcie modelowania Dodaj diagram warstwowy. Uruchom kopię diagram warstwy architektury. Możesz usunąć elementy, które nie są zależności na diagramie warstwy.  
  
       Można również dodać diagramy warstw, które reprezentują szczegółowe strukturę tej warstwy.  
  
       Te diagramy są używane do weryfikacji kodu utworzonego w tej warstwie.  
  
   4. W przypadku rozwiązania architektury edytować wymagania i modele projektu wszystkich warstw przy użyciu programu Visual Studio.  
  
       W poszczególnych rozwiązaniach warstwy opracowywanie kodu dla tej warstwy, odnoszące się do modelu. Jeśli jesteś zawartości w celu opracowywania bez korzystania z tego samego komputera do aktualizacji modelu, można odczytania modelu i tworzenie kodu za pomocą wersji programu Visual Studio, której nie można tworzyć modele. Można również wygenerować kod z modelu w tych wersjach.  
  
      Ta metoda gwarantuje, że nie zakłóceń jest spowodowana przez deweloperów, którzy edytowanie modeli warstw w tym samym czasie.  
  
      Jednak ponieważ modele są oddzielone, jest trudne do odwoływania się do typowe pojęcia. Każdy model musi mieć własną kopię elementów, na których jest on zależny od innych warstw i architektury. Diagram warstwowy w każdej warstwie musi być synchronizowana z diagram warstwy architektury. Jest trudne w utrzymaniu synchronizacji, gdy zmienią się te elementy, mimo że można tworzyć narzędzia, w tym celu.  
  
   ###### <a name="to-use-a-separate-package-for-each-layer"></a>Aby użyć oddzielny pakiet dla każdej warstwy  
  
   1. W rozwiązaniu dla każdej warstwy Dodaj projekt modelowania architektury. W Eksploratorze rozwiązań kliknij prawym przyciskiem myszy węzeł rozwiązania, wskaż opcję **Dodaj**, a następnie kliknij przycisk **istniejący projekt**. Projekt modelowania pojedynczego jest teraz dostępna z każdego rozwiązania: projekt architektury i projektu rozwoju dla każdej warstwy.  
  
   2. W udostępnionym modelu UML, należy utworzyć pakiet dla każdej warstwy: W Eksploratorze rozwiązań wybierz projekt modelowania. W Eksploratorze modelu UML, kliknij prawym przyciskiem myszy węzeł główny modelu, wskaż opcję **Dodaj**, a następnie kliknij przycisk **pakietu**.  
  
       Każdy pakiet tak, będzie zawierać diagramy UML, zawierających opis wymagań i projektowania odpowiedniej warstwy.  
  
   3. W razie potrzeby należy dodać diagramów warstwowych lokalnych dla wewnętrznej struktury każdej warstwy.  
  
      Ta metoda umożliwia elementy projektu każdej warstwy, aby odwoływać się bezpośrednio do tych warstw i popularną architekturę, od którego zależy.  
  
      Równoczesną pracą na różnych pakietach mogą powodować konflikty, są one stosunkowo łatwe do zarządzania, ponieważ te pakiety są przechowywane w oddzielnych plikach. Główne problemy jest spowodowane przez usunięcie elementu, który jest wywoływany przez pakietu zależnego. Aby uzyskać więcej informacji, zobacz [Zarządzanie modelami i diagramami w ramach kontroli wersji](../modeling/manage-models-and-diagrams-under-version-control.md).  
  
## <a name="creating-architecture-templates"></a>Tworzenie szablonów architektury  
 W praktyce nie utworzy rozwiązań programu Visual Studio w tym samym czasie, ale dodaj je w miarę postępów projektu. Prawdopodobnie będziesz również użycie tej samej struktury rozwiązania w przyszłych projektów.  Aby ułatwić szybkie tworzenie nowych rozwiązań, można utworzyć szablon rozwiązania lub projektu. Tak, aby łatwo Dystrybuuj i zainstalować na innych komputerach, można przechwycić szablonu w Visual Studio Integration rozszerzenie (VSIX).  
  
 Na przykład często używane rozwiązania mające warstwy prezentacji, biznesowych i danych, można skonfigurować szablon, który spowoduje utworzenie nowych rozwiązań, które mają tej struktury.  
  
#### <a name="to-create-a-solution-template"></a>Aby utworzyć szablon rozwiązania  
  
1.  [Pobierz i zainstaluj Kreatora eksportowania szablonu](http://go.microsoft.com/fwlink/?LinkId=196686), jeśli użytkownik jeszcze nie zostało to zrobione.  
  
2.  Tworzenie struktury rozwiązania, którego chcesz użyć jako punktu wyjścia dla przyszłych projektów.  
  
3.  Na **pliku** menu, kliknij przycisk **Eksportuj szablon jako VSIX**. **Eksportuj szablon jako Kreator VSIX** zostanie otwarty.  
  
4.  Postępując zgodnie z instrukcjami w kreatorze Wybierz projekty, które chcesz uwzględnić w szablonie, podaj nazwę i opis szablonu i określanie lokalizacji wyjściowej.  
  
> [!NOTE]
>  Materiały, w tym temacie jest wyodrębniony i paraphrased z programu Visual Studio wskazówki dotyczące narzędzi architektury, zapisanych przez program Visual Studio ALM Rangers, czyli współpracy między najbardziej cenionym specjaliści (MVP), Microsoft Services i programu Visual Studio zespół pracujący nad produktem i składników zapisywania. [Kliknij tutaj, aby pobrać kompletny pakiet wskazówek.](http://go.microsoft.com/fwlink/?LinkID=191984)  
  
## <a name="related-materials"></a>Materiały pokrewne  
 [Organizowania modeli i zarządzania nimi](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-9-Organizing-and-Managing-Your-Models/) — klip wideo od Clint Edmondson.  
  
 [Wskazówki dotyczące narzędzi architektury Studio Visual](../modeling/visual-studio-architecture-tooling-guidance.md) — dalsze wskazówki na temat zarządzania modelami w zespole  
  
## <a name="see-also"></a>Zobacz też  
 [Zarządzanie modelami i diagramami w ramach kontroli wersji](../modeling/manage-models-and-diagrams-under-version-control.md)   
 [Używanie modeli w procesie tworzenia aplikacji](../modeling/use-models-in-your-development-process.md)



