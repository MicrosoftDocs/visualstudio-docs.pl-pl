---
title: Generowanie i konfigurowanie aplikacji na podstawie modeli
description: Dowiedz się, co reprezentuje model i jak można generować lub konfigurować części aplikacji z modelu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 25a0b83d3ac7be95c42ca0c4e53a188569bb5770
ms.sourcegitcommit: 4d394866b7817689411afee98e85da1653ec42f2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/12/2020
ms.locfileid: "97361875"
---
# <a name="generate-and-configure-your-app-from-models"></a>Generowanie i konfigurowanie aplikacji na podstawie modeli
Można generować lub konfigurować części aplikacji z modelu.

 Model reprezentuje wymagania bezpośrednio od kodu. Dzięki wykorzystaniu zachowania aplikacji bezpośrednio z modelu, można reagować na zmienione wymagania znacznie szybciej i niezawodnie niż przez aktualizację kodu. Chociaż wymaga się, aby skonfigurować wyprowadzanie, ta inwestycja jest zwracana, jeśli oczekujesz zmian w wymaganiach lub jeśli planujesz kilka wariantów produktu.

## <a name="generating-the-code-of-your-application-from-a-model"></a>Generowanie kodu aplikacji z modelu
 Najprostszym sposobem generowania kodu jest użycie szablonów tekstowych. Można wygenerować kod w tym samym rozwiązaniu programu Visual Studio, w którym zachowujesz model. Aby uzyskać więcej informacji, zobacz:

- [Generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)

- [Generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md)

  Ta metoda jest łatwa do zastosowania przyrostowo. Zacznij od aplikacji, która działa tylko w konkretnym przypadku, i wybierz kilka części, które mają być różne w zależności od modelu. Zmień nazwy plików źródłowych tych części tak, aby znajdowały się na pliki szablonów tekstowych (. tt). W tym momencie źródłowe pliki. cs zostaną automatycznie wygenerowane na podstawie plików szablonów, dzięki czemu aplikacja będzie działać tak jak wcześniej.

  Następnie można wykonać jedną część kodu i zastąpić ją wyrażeniem szablonu tekstu, które odczytuje model i generuje tę część pliku źródłowego. Co najmniej jedna wartość modelu powinna generować oryginalne źródło, aby można było uruchomić aplikację i będzie działać tak jak wcześniej. Po przetestowaniu różnych wartości modelu można przenieść się, aby wstawić wyrażenia szablonu w innej części kodu.

  Ta metoda przyrostowa oznacza, że generowanie kodu jest zwykle podejściem niskiego ryzyka. Aplikacje, które są zwykle wykonywane niemal, również są w wersji zaręcznej.

  Jeśli jednak zaczniesz od istniejącej aplikacji, może się okazać, że wiele refaktoryzacji jest wymagane do oddzielenia różnych zachowań, które są regulowane przez model, aby można było je niezależnie zmieniać. Zalecamy ocenę tego aspektu aplikacji podczas szacowania kosztów projektu.

## <a name="configuring-your-application-from-a-model"></a>Konfigurowanie aplikacji z modelu
 Jeśli chcesz zmienić zachowanie aplikacji w czasie wykonywania, nie możesz użyć generowania kodu, który generuje kod źródłowy przed skompilowaniem aplikacji. Zamiast tego można zaprojektować aplikację w celu odczytania modelu i odpowiednio zmienić jej zachowanie. Aby uzyskać więcej informacji, zobacz:

- [Porady: otwieranie modelu z pliku w kodzie programu](../modeling/how-to-open-a-model-from-file-in-program-code.md)

  Ta metoda może być również stosowana przyrostowo, ale na początku występuje więcej pracy. Należy napisać kod, który będzie odczytywać model, i skonfigurować platformę, która umożliwia dostęp do elementów zmiennych. Tworzenie części zmiennych ogólnych jest droższe niż generowanie kodu.

  Aplikacja ogólna zazwyczaj wykonuje mniej dobrze niż jej określone odpowiedniki. Jeśli wydajność jest istotna, plan projektu powinien zawierać ocenę tego ryzyka.

## <a name="developing-a-derived-application"></a>Tworzenie aplikacji pochodnej
 Poniżej przedstawiono ogólne wytyczne.

- **Rozpocznij określony, a następnie Uogólnij.** Najpierw Napisz konkretną wersję aplikacji. Ta wersja powinna współpracować z jednym zestawem warunków. Po upewnieniu się, że działa prawidłowo, można sprawić, że niektóre z nich pochodzą z modelu. Stopniowo Poszerzaj części pochodne.

     Na przykład Zaprojektuj witrynę sieci Web, która ma określony zestaw stron sieci Web, przed zaprojektowaniem aplikacji internetowej, która przedstawia strony zdefiniowane w modelu.

- **Modelowanie aspektów wariantów.** Określ aspekty, które będą się różnić, między jednym wdrożeniem a innym lub w czasie, gdy zmienią się wymagania. Są to aspekty, które powinny pochodzić z modelu.

     Na przykład jeśli zestaw stron sieci Web i linki między nimi zmienią się, ale styl i format stron są zawsze takie same, wówczas model powinien opisać linki, ale nie musi opisywać formatu stron.

- **Oddzielne zagadnienia.** Jeśli zmienne aspekty można podzielić na niezależne obszary, użyj oddzielnych modeli dla każdego obszaru. Za pomocą ModelBus można definiować operacje, które mają wpływ na modele i ograniczenia między nimi.

     Na przykład użyj jednego modelu do zdefiniowania nawigacji między stronami sieci Web a innym modelem w celu zdefiniowania układu stron.

- **Modeluje to wymaganie, a nie rozwiązanie.** Zaprojektuj model w taki sposób, aby opisuje wymagania użytkownika. Z kolei nie należy projektować notacji zgodnie ze zmiennymi aspektami implementacji.

     Na przykład model nawigacji sieci Web powinien reprezentować strony sieci Web i hiperłącza między nimi. Model nawigacyjny sieci Web nie powinien reprezentować fragmentów kodu HTML ani klas w aplikacji.

- **Czy generować lub interpretować?** Jeśli wymagania dotyczące określonego wdrożenia będą rzadko zmieniane, należy wygenerować kod programu z modelu. Jeśli wymagania mogą być często zmieniane lub mogą współistnieć w więcej niż jednym elemencie Variant w tym samym wdrożeniu, napisz aplikację tak, aby mogła ona odczytywać i interpretować model.

     Na przykład, jeśli używasz modelu witryny sieci Web do tworzenia serii różnych i oddzielnie zainstalowanych witryn sieci Web, należy wygenerować kod lokacji z modelu. Ale przy użyciu modelu można kontrolować lokację, która zmienia się codziennie, lepiej jest napisać serwer sieci Web, który odczytuje model i odpowiednio przedstawia lokację.

- **UML lub DSL?** Rozważ utworzenie notacji modelowania przy użyciu stereotypów, aby zwiększyć UML. Zdefiniuj DSL, jeśli nie ma diagramu UML pasującego do tego celu. Należy jednak unikać przerywania standardowej semantyki UML.

     Na przykład Diagram klas UML jest kolekcją pól i strzałek; za pomocą tej notacji można określić wszystko. Nie zaleca się jednak używania diagramu klas, z wyjątkiem sytuacji, w których fakt opisywania zestawu typów. Na przykład można dostosować diagramy klas do opisywania różnych typów stron sieci Web.

## <a name="see-also"></a>Zobacz też

- [Generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md)
- [Porady: otwieranie modelu z pliku w kodzie programu](../modeling/how-to-open-a-model-from-file-in-program-code.md)
- [Generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)
