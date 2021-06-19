---
title: Tworzenie struktury rozwiązania modelowania
description: Poznaj schemat modelowania do dzielenia aplikacji na różne części, które odpowiadają warstwom na ogólnym diagramie warstwowym.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 54275c55d3d7a80dc2df1721585bc6c39ba8b06e
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385490"
---
# <a name="structure-your-modeling-solution"></a>Tworzenie struktury rozwiązania modelowania

Aby efektywnie korzystać z modeli w projekcie dewelopera, członkowie zespołu muszą mieć możliwość pracy nad modelami różnych części projektu w tym samym czasie. Ten temat sugeruje schemat dzielenia aplikacji na różne części, które odpowiadają warstwom na ogólnym diagramie warstwowym.

Aby szybko rozpocząć od projektu lub podprojektu, warto mieć szablon projektu zgodny ze wybraną strukturą projektu. W tym temacie opisano sposób tworzenia i używania takiego szablonu.

W tym temacie przyjęto założenie, że pracujesz nad projektem, który jest wystarczająco duży, aby wymagać kilku członków zespołu i może mieć kilka zespołów. Kod i modele projektu są przechowywane w systemie kontroli źródła, takim jak [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] . Co najmniej niektórzy członkowie zespołu używają Visual Studio do tworzenia modeli, a inni członkowie zespołu mogą wyświetlać modele przy użyciu innych Visual Studio wersji.

Aby sprawdzić, które wersje Visual Studio obsługują poszczególne narzędzia i funkcje modelowania, zobacz Obsługa wersji dla architektury i [narzędzi do modelowania.](../modeling/analyze-and-model-your-architecture.md#VersionSupport)

## <a name="solution-structure"></a>Struktura rozwiązania

W średnim lub dużym projekcie struktura zespołu jest oparta na strukturze aplikacji. Każdy zespół używa Visual Studio rozwiązania.

### <a name="to-divide-an-application-into-layers"></a>Aby podzielić aplikację na warstwy

1. Strukturę rozwiązań należy opierać na strukturze aplikacji, na przykład aplikacji internetowej, aplikacji usługi lub aplikacji klasycznej. Różne typowe architektury zostały omówione w artykule [Application Archetypes (Archetypy](/previous-versions/msp-n-p/ee658107(v=pandp.10))aplikacji) w przewodniku po architekturze aplikacji firmy Microsoft.

2. Utwórz Visual Studio, które będziemy nazywać rozwiązaniem Architecture. To rozwiązanie zostanie użyte do utworzenia ogólnego projektu systemu. Będzie ona zawierać modele, ale nie będzie zawierać kodu.

   Dodaj diagram zależności do tego rozwiązania. Na diagramie zależności narysuj architekturę wybraną dla aplikacji. Na przykład diagram może przedstawiać te warstwy i zależności między nimi: Prezentacja; Logika biznesowa; i Dane.

4. Utwórz oddzielne rozwiązanie Visual Studio dla każdej warstwy na diagramie zależności Architektura.

   Te rozwiązania będą używane do opracowywania kodu warstw.

5. Tworzenie modeli reprezentujących projekty warstw i koncepcje wspólne dla wszystkich warstw. Rozmieść modele tak, aby wszystkie modele można było zobaczyć w rozwiązaniu Architecture, a odpowiednie modele można zobaczyć z każdej warstwy.

   Można to osiągnąć, korzystając z jednej z poniższych procedur. Pierwsza alternatywa tworzy oddzielny projekt modelowania dla każdej warstwy, a druga tworzy pojedynczy projekt modelowania, który jest współużytkowany między warstwami.

#### <a name="use-a-separate-modeling-project-for-each-layer"></a>Używanie oddzielnego projektu modelowania dla każdej warstwy

1. Utwórz projekt modelowania w każdym rozwiązaniu warstwowym.

   Ten model będzie zawierać diagramy opisujące wymagania i projekt tej warstwy. Może również zawierać diagramy zależności, które pokazują zagnieżdżone warstwy.

   Masz teraz model dla każdej warstwy oraz model dla architektury aplikacji. Każdy model jest zawarty we własnym rozwiązaniu. Dzięki temu członkowie zespołu mogą pracować nad warstwami w tym samym czasie.

2. Do rozwiązania Architecture (Architektura) dodaj projekt modelowania poszczególnych rozwiązań warstwowych. W tym celu otwórz rozwiązanie Architektura. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy węzeł rozwiązania, wskaż polecenie Dodaj, a następnie kliknij pozycję **Istniejący projekt**. Przejdź do projektu modelowania (.modelproj) w rozwiązaniu jednowarstwowym.

   Każdy model jest teraz widoczny w dwóch rozwiązaniach: "home" i architecture.

3. Do projektu modelowania każdej warstwy dodaj diagram zależności. Zacznij od kopii diagramu zależności Architektura. Możesz usunąć części, które nie są zależnościami diagramu zależności.

   Można również dodać diagramy zależności, które reprezentują szczegółową strukturę tej warstwy.

   Te diagramy służą do weryfikowania kodu opracowywanego w tej warstwie.

4. W rozwiązaniu Architektura edytuj wymagania i modele projektowe wszystkich warstw przy użyciu Visual Studio.

   W każdym rozwiązaniu warstwowym opracuj kod dla tej warstwy, odwołując się do modelu. Jeśli jesteś zadedyowany, aby tworzyć oprogramowanie bez używania tego samego komputera do aktualizowania modelu, możesz odczytać model i opracować kod przy użyciu wersji programu Visual Studio, które nie mogą tworzyć modeli. W tych wersjach można również wygenerować kod z modelu.

   Ta metoda gwarantuje, że deweloperzy, którzy edytują modele warstw w tym samym czasie, nie będą powodować żadnych zakłóceń.

   Jednak ze względu na to, że modele są oddzielne, trudno jest odwołać się do typowych pojęć. Każdy model musi mieć własną kopię elementów, od których jest zależny od innych warstw i architektury. Diagram zależności w każdej warstwie musi być zsynchronizowany z diagramem zależności Architektura. Trudno jest zachować synchronizację, gdy te elementy się zmieniają, chociaż można opracować narzędzia, aby to osiągnąć.

#### <a name="use-a-separate-package-for-each-layer"></a>Używanie oddzielnego pakietu dla każdej warstwy

1. W rozwiązaniu dla każdej warstwy dodaj projekt Modelowanie architektury. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy węzeł rozwiązania, wskaż polecenie **Dodaj,** a następnie kliknij pozycję **Istniejący projekt**. Dostęp do pojedynczego projektu modelowania można teraz uzyskać z każdego rozwiązania: projektu Architecture i projektu programowego dla każdej warstwy.

2. W modelu udostępnionym utwórz pakiet dla każdej warstwy: w Eksplorator rozwiązań **wybierz** projekt modelowania. W **Eksploratorze modeli UML** kliknij prawym przyciskiem myszy węzeł główny modelu, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **Spakuj**.

   Każdy pakiet będzie zawierać diagramy opisujące wymagania i projekt odpowiedniej warstwy.

3. W razie potrzeby dodaj lokalne diagramy zależności dla wewnętrznej struktury każdej warstwy.

   Ta metoda umożliwia elementom projektu każdej warstwy bezpośrednie odwołujące się do warstw i wspólnej architektury, od której zależy.

   Mimo że współbieżne prace nad różnymi pakietami mogą powodować konflikty, zarządzanie nimi jest dość proste, ponieważ pakiety są przechowywane w oddzielnych plikach.

## <a name="create-architecture-templates"></a>Tworzenie szablonów architektury

W praktyce nie tworzysz wszystkich swoich rozwiązań Visual Studio w tym samym czasie, ale dodajesz je w trakcie realizacji projektu. Prawdopodobnie będziesz również używać tej samej struktury rozwiązania w przyszłych projektach. Aby ułatwić szybkie tworzenie nowych rozwiązań, możesz utworzyć rozwiązanie lub szablon projektu. Szablon można przechwycić w pliku Visual Studio Integration Extension (VSIX), aby można go było łatwo dystrybuować i instalować na innych komputerach.

Jeśli na przykład często używasz rozwiązań z warstwami Prezentacja, Firma i Dane, możesz skonfigurować szablon, który utworzy nowe rozwiązania o tej strukturze.

### <a name="to-create-a-solution-template"></a>Aby utworzyć szablon rozwiązania

1. [Pobierz i zainstaluj Kreatora eksportowania szablonu.](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.ExportTemplateWizard)

2. Utwórz strukturę rozwiązania, której chcesz użyć jako punktu wyjścia dla przyszłych projektów.

3. W menu **File (Plik)** kliknij pozycję **Export Template as VSIX (Eksportuj szablon jako VSIX).**

   Zostanie **otwarty Kreator eksportowania szablonu jako VSIX.**

4. Zgodnie z instrukcjami w kreatorze wybierz projekty, które chcesz uwzględnić w szablonie, podaj nazwę i opis szablonu oraz określ lokalizację wyjściową.

## <a name="watch-a-video"></a>Obejrzyj film

[Organizowanie modeli i zarządzanie nimi](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-9-organizing-and-managing-your-models)

## <a name="see-also"></a>Zobacz też

- [Używanie modeli w procesie tworzenia aplikacji](../modeling/use-models-in-your-development-process.md)
