---
title: Tworzenie struktury rozwiązania modelowania
description: Poznaj schemat modelowania służący do dzielenia aplikacji na różne części, które odpowiadają warstwom na ogólnym diagramie warstwowym.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9d2f865cf66da0bb4496a3d754a49d1f4dcc70ff
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2020
ms.locfileid: "97363734"
---
# <a name="structure-your-modeling-solution"></a>Tworzenie struktury rozwiązania modelowania

Aby efektywnie korzystać z modeli w projekcie deweloperskim, członkowie zespołu muszą mieć możliwość pracy nad modelami różnych części projektu w tym samym czasie. W tym temacie zawarto schemat dzielenia aplikacji na różne części, które odpowiadają warstwom na ogólnym diagramie warstwowym.

Aby szybko rozpocząć pracę nad projektem lub podprojektem, warto mieć szablon projektu, który następuje po wybranej strukturze projektu. W tym temacie opisano sposób tworzenia i używania takiego szablonu.

W tym temacie założono, że pracujesz nad projektem, który jest wystarczająco duży, aby wymagać kilku członków zespołu, a może mieć kilka zespołów. Kod i modele projektu są przechowywane w systemie kontroli źródła, takich jak [!INCLUDE[esprtfs](../code-quality/includes/esprtfs_md.md)] . Co najmniej niektórzy członkowie zespołu używają programu Visual Studio do tworzenia modeli, a inni członkowie zespołu mogą wyświetlać modele przy użyciu innych wersji programu Visual Studio.

Aby sprawdzić, które wersje programu Visual Studio obsługują poszczególne narzędzia i funkcje modelowania, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="solution-structure"></a>Struktura rozwiązania

W średnim lub dużym projekcie struktura zespołu opiera się na strukturze aplikacji. Każdy zespół używa rozwiązania programu Visual Studio.

### <a name="to-divide-an-application-into-layers"></a>Aby podzielić aplikację na warstwy

1. Podstawowe struktury rozwiązań na podstawie struktury aplikacji, takiej jak aplikacja sieci Web, aplikacja usługi lub aplikacja klasyczna. Wiele typowych architektur omówiono w temacie [Application Archetypes w przewodniku po architekturze aplikacji firmy Microsoft](/previous-versions/msp-n-p/ee658107(v=pandp.10)).

2. Utwórz rozwiązanie programu Visual Studio, które wywoła rozwiązanie architektury. To rozwiązanie zostanie użyte do utworzenia ogólnego projektu systemu. Będzie zawierać modele, ale nie kod.

   Dodaj diagram zależności do tego rozwiązania. Na diagramie zależności należy narysować architekturę wybraną dla aplikacji. Na przykład diagram może pokazać te warstwy i zależności między nimi: Prezentacja; Logika biznesowa; i dane.

4. Utwórz oddzielne rozwiązanie programu Visual Studio dla każdej warstwy na diagramie zależności architektury.

   Te rozwiązania zostaną użyte do opracowania kodu warstw.

5. Utwórz modele, które reprezentują projekty warstw i pojęcia, które są wspólne dla wszystkich warstw. Rozmieść modele w taki sposób, aby wszystkie modele mogły być widoczne z rozwiązania architektury, a odpowiednie modele można zobaczyć z każdej warstwy.

   Można to osiągnąć za pomocą jednej z poniższych procedur. Pierwsza alternatywa tworzy oddzielny projekt modelowania dla każdej warstwy, a drugi tworzy pojedynczy projekt modelowania, który jest współużytkowany między warstwami.

#### <a name="use-a-separate-modeling-project-for-each-layer"></a>Użyj oddzielnego projektu modelowania dla każdej warstwy

1. Utwórz projekt modelowania w poszczególnych rozwiązaniach warstwowych.

   Ten model będzie zawierać diagramy opisujące wymagania i projekt tej warstwy. Może również zawierać diagramy zależności pokazujące warstwy zagnieżdżone.

   Teraz masz model dla każdej warstwy oraz model architektury aplikacji. Każdy model jest zawarty we własnym rozwiązaniu. Dzięki temu członkowie zespołu mogą korzystać z warstw w tym samym czasie.

2. Do rozwiązania architektury Dodaj projekt modelowania dla każdego rozwiązania warstwy. Aby to zrobić, Otwórz rozwiązanie architektury. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy węzeł rozwiązanie, wskaż polecenie Dodaj, a następnie kliknij pozycję **istniejący projekt**. Przejdź do projektu modelowania (. modelproj) w jednym rozwiązaniu warstwy.

   Każdy model jest teraz widoczny w dwóch rozwiązaniach: jego rozwiązanie "Home" i rozwiązanie architektury.

3. Do projektu modelowania każdej warstwy Dodaj diagram zależności. Zacznij od kopii diagramu zależności architektury. Można usunąć części, które nie są zależnościami diagramu zależności.

   Można również dodać diagramy zależności, które reprezentują szczegółową strukturę tej warstwy.

   Te diagramy służą do sprawdzania poprawności kodu opracowanego w tej warstwie.

4. W rozwiązaniu architektury Zmień wymagania i modele projektu wszystkich warstw przy użyciu programu Visual Studio.

   W każdym rozwiązaniu warstwy Utwórz kod dla tej warstwy, odnoszący się do modelu. Jeśli zawartość ma zostać wdrożona bez użycia tego samego komputera do zaktualizowania modelu, można odczytać model i opracować kod przy użyciu wersji programu Visual Studio, które nie mogą tworzyć modeli. Możesz również wygenerować kod z modelu w tych wersjach.

   Ta metoda gwarantuje, że żadne zakłócenia nie będzie spowodowane przez deweloperów, którzy edytują modele warstwy w tym samym czasie.

   Jednak ze względu na to, że modele są oddzielne, trudno jest odwoływać się do typowych koncepcji. Każdy model musi mieć własną kopię elementów, od których jest zależna od innych warstw i architektury. Diagram zależności w każdej warstwie musi być zsynchronizowany z diagramem zależności architektury. W przypadku zmiany tych elementów trudno jest zachować synchronizację, chociaż można opracowywać narzędzia do osiągnięcia tego celu.

#### <a name="use-a-separate-package-for-each-layer"></a>Użyj oddzielnego pakietu dla każdej warstwy

1. W rozwiązaniu dla każdej warstwy Dodaj projekt z modelem architektury. W **Eksplorator rozwiązań** kliknij prawym przyciskiem myszy węzeł rozwiązanie, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **istniejący projekt**. Dostęp do pojedynczego projektu modelowania można teraz uzyskać z każdego rozwiązania: projektu architektury i projektu deweloperskiego dla każdej warstwy.

2. W modelu udostępnionym Utwórz pakiet dla każdej warstwy: w **Eksplorator rozwiązań** wybierz projekt modelowania. W **Eksploratorze modelu UML** kliknij prawym przyciskiem myszy węzeł główny modelu, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **pakiet**.

   Każdy pakiet będzie zawierać diagramy opisujące wymagania i projekt odpowiedniej warstwy.

3. W razie potrzeby Dodaj lokalne diagramy zależności dla wewnętrznej struktury każdej warstwy.

   Dzięki tej metodzie elementy projektu każdej warstwy mogą odwoływać się bezpośrednio do tych warstw i wspólnych architektur, na których jest ona zależna.

   Mimo że współbieżna współpraca nad różnymi pakietami może spowodować pewne konflikty, są one dość łatwe do zarządzania, ponieważ pakiety są przechowywane w oddzielnych plikach.

## <a name="create-architecture-templates"></a>Tworzenie szablonów architektury

W tej chwili nie utworzysz jednocześnie wszystkich rozwiązań programu Visual Studio, ale dodajesz je w miarę postępów projektu. Prawdopodobnie będziesz również używać tej samej struktury rozwiązań w przyszłych projektach. Aby szybko tworzyć nowe rozwiązania, można utworzyć rozwiązanie lub szablon projektu. Szablon można przechwycić w rozszerzeniu integracji programu Visual Studio (VSIX), aby ułatwić dystrybucję i instalację na innych komputerach.

Jeśli na przykład często używasz rozwiązań z warstwami prezentacji, firmowych i danych, możesz skonfigurować szablon, który będzie tworzyć nowe rozwiązania mające tę strukturę.

### <a name="to-create-a-solution-template"></a>Aby utworzyć szablon rozwiązania

1. [Pobierz i zainstaluj Kreatora eksportu szablonów](https://marketplace.visualstudio.com/items?itemName=VisualStudioProductTeam.ExportTemplateWizard).

2. Utwórz strukturę rozwiązania, która ma być używana jako punkt wyjścia dla przyszłych projektów.

3. W menu **plik** kliknij polecenie **Eksportuj szablon jako VSIX**.

   Zostanie otwarty **Kreator eksportowania szablonu jako VSIX** .

4. Postępując zgodnie z instrukcjami wyświetlanymi w kreatorze, wybierz projekty, które chcesz uwzględnić w szablonie, podaj nazwę i opis szablonu, a następnie określ lokalizację wyjściową.

## <a name="watch-a-video"></a>Obejrzyj film

[Organizowanie modeli i zarządzanie nimi](https://channel9.msdn.com/blogs/clinted/uml-with-vs-2010-part-9-organizing-and-managing-your-models)

## <a name="see-also"></a>Zobacz też

- [Używanie modeli w procesie tworzenia aplikacji](../modeling/use-models-in-your-development-process.md)
- [Architektura Visual Studio — wskazówki dotyczące oprzyrządowania](../modeling/visual-studio-architecture-tooling-guidance.md)
