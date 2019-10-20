---
title: Tworzenie struktury rozwiązania do modelowania | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
ms.assetid: 2ba70ba4-2cea-4e01-93c2-055903d59470
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: edf9eaee512eda7439d1beea7303cd0e74b27178
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72661040"
---
# <a name="structure-your-modeling-solution"></a>Tworzenie struktury rozwiązania modelowania

[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby efektywnie korzystać z modeli w projekcie deweloperskim, członkowie zespołu muszą mieć możliwość pracy nad modelami różnych części projektu w tym samym czasie. W tym temacie zawarto schemat dzielenia aplikacji na różne części, które odpowiadają warstwom na ogólnym diagramie warstwowym.

Aby szybko rozpocząć pracę nad projektem lub podprojektem, warto mieć szablon projektu, który następuje po wybranej strukturze projektu. W tym temacie opisano sposób tworzenia i używania takiego szablonu.

W tym temacie założono, że pracujesz nad projektem, który jest wystarczająco duży, aby wymagać kilku członków zespołu, a może mieć kilka zespołów. Kod i modele projektu są przechowywane w systemie kontroli źródła, takim jak [!INCLUDE[esprtfs](../includes/esprtfs-md.md)]. Co najmniej niektórzy członkowie zespołu używają programu Visual Studio do tworzenia modeli, a inni członkowie zespołu mogą wyświetlać modele przy użyciu innych wersji programu Visual Studio.

Aby sprawdzić, które wersje programu Visual Studio obsługują poszczególne narzędzia i funkcje modelowania, zobacz [Obsługa wersji dla narzędzi architektury i modelowania](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

## <a name="solution-structure"></a>Struktura rozwiązania

W średnim lub dużym projekcie struktura zespołu opiera się na strukturze aplikacji. Każdy zespół używa rozwiązania programu Visual Studio.

#### <a name="to-divide-an-application-into-layers"></a>Aby podzielić aplikację na warstwy

1. Podstawowe struktury rozwiązań na podstawie struktury aplikacji, takiej jak aplikacja sieci Web, aplikacja usługi lub aplikacja klasyczna. Wiele typowych architektur omówiono w temacie [Application Archetypes w przewodniku po architekturze aplikacji firmy Microsoft](http://go.microsoft.com/fwlink/?LinkId=196681).

2. Utwórz rozwiązanie [!INCLUDE[vsprvs](../includes/vsprvs-md.md)], które wywoła rozwiązanie architektury. To rozwiązanie zostanie użyte do utworzenia ogólnego projektu systemu. Będzie zawierać modele, ale nie kod.

    Dodaj diagram warstwowy do tego rozwiązania. Na diagramie warstwy narysuj architekturę wybraną dla aplikacji. Na przykład diagram może pokazać te warstwy i zależności między nimi: Prezentacja; Logika biznesowa; i dane.

    Diagram warstwowy i nowe rozwiązanie programu Visual Studio można utworzyć w tym samym czasie przy użyciu **nowego UML lub polecenia diagramu warstwowego** w menu **Architektura** .

3. Dodaj do diagramów UML modelu architektury, które reprezentują ważne koncepcje biznesowe i przypadki użycia, które są określane w projekcie wszystkich warstw.

4. Utwórz oddzielne rozwiązanie programu Visual Studio dla każdej warstwy na diagramie warstwy architektury.

    Te rozwiązania zostaną użyte do opracowania kodu warstw.

5. Utwórz modele UML, które będą reprezentować projekty warstw i pojęcia, które są wspólne dla wszystkich warstw. Rozmieść modele w taki sposób, aby wszystkie modele mogły być widoczne z rozwiązania architektury, a odpowiednie modele można zobaczyć z każdej warstwy.

    Można to osiągnąć za pomocą jednej z poniższych procedur. Pierwsza alternatywa tworzy oddzielny projekt modelowania dla każdej warstwy, a drugi tworzy pojedynczy projekt modelowania, który jest współużytkowany między warstwami.

###### <a name="to-use-a-separate-modeling-project-for-each-layer"></a>Aby użyć oddzielnego projektu modelowania dla każdej warstwy

1. Utwórz projekt modelowania w poszczególnych rozwiązaniach warstwowych.

    Ten model będzie zawierać diagramy UML opisujące wymagania i projekt tej warstwy. Może również zawierać diagramy warstwowe, które pokazują warstwy zagnieżdżone.

    Teraz masz model dla każdej warstwy oraz model architektury aplikacji. Każdy model jest zawarty we własnym rozwiązaniu. Dzięki temu członkowie zespołu mogą korzystać z warstw w tym samym czasie.

2. Do rozwiązania architektury Dodaj projekt modelowania dla każdego rozwiązania warstwy. Aby to zrobić, Otwórz rozwiązanie architektury. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy węzeł rozwiązanie, wskaż polecenie Dodaj, a następnie kliknij pozycję **istniejący projekt**. Przejdź do projektu modelowania (. modelproj) w jednym rozwiązaniu warstwy.

    Każdy model jest teraz widoczny w dwóch rozwiązaniach: jego rozwiązanie "Home" i rozwiązanie architektury.

3. Do projektu modelowania każdej warstwy, Dodaj diagram warstwowy. Zacznij od kopii diagramu warstwy architektury. Można usunąć części, które nie są zależnościami diagramu warstwowego.

    Możesz również dodać diagramy warstwowe, które reprezentują szczegółową strukturę tej warstwy.

    Te diagramy służą do sprawdzania poprawności kodu opracowanego w tej warstwie.

4. W rozwiązaniu architektury Zmień wymagania i modele projektu wszystkich warstw przy użyciu programu Visual Studio.

    W każdym rozwiązaniu warstwy Utwórz kod dla tej warstwy, odnoszący się do modelu. Jeśli zawartość ma zostać wdrożona bez użycia tego samego komputera do zaktualizowania modelu, można odczytać model i opracować kod przy użyciu wersji programu Visual Studio, które nie mogą tworzyć modeli. Możesz również wygenerować kod z modelu w tych wersjach.

    Ta metoda gwarantuje, że żadne zakłócenia nie będzie spowodowane przez deweloperów, którzy edytują modele warstwy w tym samym czasie.

    Jednak ze względu na to, że modele są oddzielne, trudno jest odwoływać się do typowych koncepcji. Każdy model musi mieć własną kopię elementów, od których jest zależna od innych warstw i architektury. Diagram warstwy w każdej warstwie musi być zsynchronizowany z diagramem warstwy architektury. W przypadku zmiany tych elementów trudno jest zachować synchronizację, chociaż można opracowywać narzędzia do osiągnięcia tego celu.

###### <a name="to-use-a-separate-package-for-each-layer"></a>Aby użyć oddzielnego pakietu dla każdej warstwy

1. W rozwiązaniu dla każdej warstwy Dodaj projekt z modelem architektury. W Eksplorator rozwiązań kliknij prawym przyciskiem myszy węzeł rozwiązanie, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **istniejący projekt**. Dostęp do pojedynczego projektu modelowania można teraz uzyskać z każdego rozwiązania: projektu architektury i projektu deweloperskiego dla każdej warstwy.

2. W udostępnionym modelu UML Utwórz pakiet dla każdej warstwy: w Eksplorator rozwiązań wybierz projekt modelowania. W Eksploratorze modelu UML kliknij prawym przyciskiem myszy węzeł główny modelu, wskaż polecenie **Dodaj**, a następnie kliknij pozycję **pakiet**.

    Każdy pakiet będzie zawierać diagramy UML opisujące wymagania i projekt odpowiedniej warstwy.

3. W razie potrzeby Dodaj diagramy warstwy lokalnej dla wewnętrznej struktury każdej warstwy.

    Dzięki tej metodzie elementy projektu każdej warstwy mogą odwoływać się bezpośrednio do tych warstw i wspólnych architektur, na których jest ona zależna.

    Mimo że współbieżna współpraca nad różnymi pakietami może spowodować pewne konflikty, są one dość łatwe do zarządzania, ponieważ pakiety są przechowywane w oddzielnych plikach. Zasadnicze trudności wynikają z usunięcia elementu, do którego odwołuje się pakiet zależny. Aby uzyskać więcej informacji, zobacz [Zarządzanie modelami i diagramami w obszarze kontroli wersji](../modeling/manage-models-and-diagrams-under-version-control.md).

## <a name="creating-architecture-templates"></a>Tworzenie szablonów architektury

W tej chwili nie utworzysz jednocześnie wszystkich rozwiązań programu Visual Studio, ale zostaną one dodane jako postęp projektu. Prawdopodobnie będziesz również używać tej samej struktury rozwiązań w przyszłych projektach.  Aby szybko tworzyć nowe rozwiązania, można utworzyć rozwiązanie lub szablon projektu. Szablon można przechwycić w rozszerzeniu integracji programu Visual Studio (VSIX), aby ułatwić dystrybucję i instalację na innych komputerach.

Jeśli na przykład często używasz rozwiązań z warstwami prezentacji, firmowych i danych, możesz skonfigurować szablon, który będzie tworzyć nowe rozwiązania mające tę strukturę.

#### <a name="to-create-a-solution-template"></a>Aby utworzyć szablon rozwiązania

1. [Pobierz i zainstaluj Kreatora eksportu szablonów](http://go.microsoft.com/fwlink/?LinkId=196686), jeśli jeszcze tego nie zrobiono.

2. Utwórz strukturę rozwiązania, która ma być używana jako punkt wyjścia dla przyszłych projektów.

3. W menu **plik** kliknij polecenie **Eksportuj szablon jako VSIX**. Zostanie otwarty **Kreator eksportowania szablonu jako VSIX** .

4. Postępując zgodnie z instrukcjami wyświetlanymi w kreatorze, wybierz projekty, które chcesz uwzględnić w szablonie, podaj nazwę i opis szablonu, a następnie określ lokalizację wyjściową.

> [!NOTE]
> Materiał przedstawiony w tym temacie jest abstrakcyjny i paraphrased ze wskazówkami dotyczącymi narzędzi architektury programu Visual Studio, które są napisywane przez zakresy ALM programu Visual Studio, które są współdziałaniem między profesjonalistami (MVP), usługami firmy Microsoft i programem Visual Studio zespół produktu i autorzy. [Kliknij tutaj, aby pobrać kompletny pakiet wskazówek.](http://go.microsoft.com/fwlink/?LinkID=191984)

## <a name="related-materials"></a>Powiązane materiały

Organizowanie modeli — wideo według Clint Edmondson [i zarządzanie nimi](http://channel9.msdn.com/posts/clinted/UML-with-VS-2010-Part-9-Organizing-and-Managing-Your-Models/) .

[Wskazówki dotyczące narzędzi architektury programu Visual Studio](../modeling/visual-studio-architecture-tooling-guidance.md) — dalsze wskazówki dotyczące zarządzania modelami w zespole

## <a name="see-also"></a>Zobacz też

[Zarządzanie modelami i diagramami w ramach kontroli wersji](../modeling/manage-models-and-diagrams-under-version-control.md) 
[używać modeli w procesie programistycznym](../modeling/use-models-in-your-development-process.md)
