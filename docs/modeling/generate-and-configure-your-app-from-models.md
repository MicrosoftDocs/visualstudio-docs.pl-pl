---
title: Generowanie i konfigurowanie aplikacji na podstawie modeli
description: Dowiedz się, co reprezentuje model i jak można generować lub konfigurować części aplikacji na podstawie modelu.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 68339159ed9926490f22a82cd30ce69f45ab6a30
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112388870"
---
# <a name="generate-and-configure-your-app-from-models"></a>Generowanie i konfigurowanie aplikacji na podstawie modeli
Części aplikacji można generować lub konfigurować na podstawie modelu.

 Model reprezentuje wymagania bardziej bezpośrednio niż kod. Wyprowadzając zachowanie aplikacji bezpośrednio z modelu, możesz reagować na zmienione wymagania znacznie szybciej i niezawodniej niż przez zaktualizowanie kodu. Mimo że do skonfigurowania wyprowadzenia wymagana jest wstępna praca, ta inwestycja jest zwracana, jeśli spodziewasz się zmian wymagań lub jeśli planujesz wprowadzić kilka wariantów produktu.

## <a name="generating-the-code-of-your-application-from-a-model"></a>Generowanie kodu aplikacji z modelu
 Najprostszym sposobem generowania kodu jest użycie szablonów tekstowych. Kod można wygenerować w tym samym Visual Studio, w którym jest zachowanie modelu. Aby uzyskać więcej informacji, zobacz:

- [Generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)

- [Generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md)

  Ta metoda jest łatwa do zastosowania przyrostowo. Zacznij od aplikacji, która działa tylko w konkretnym przypadku, i wybierz kilka jej części, które mają się różnić od modelu. Zmień nazwy plików źródłowych tych części, tak aby stały się plikami szablonu tekstowego (tt). W tym momencie źródłowe pliki cs zostaną automatycznie wygenerowane na podstawie plików szablonów, więc aplikacja będzie działać tak jak wcześniej.

  Następnie możesz użyć jednej części kodu i zastąpić ją wyrażeniem szablonu tekstowego, które odczytuje model i generuje ją w pliku źródłowym. Co najmniej jedna wartość modelu powinna wygenerować oryginalne źródło, aby można było ponownie uruchomić aplikację i będzie ona działać tak jak poprzednio. Po przetestowaniu różnych wartości modelu możesz przejść do wstawiania wyrażeń szablonu w innej części kodu.

  Ta metoda przyrostowa oznacza, że generowanie kodu jest zwykle podejściem o niskim ryzyku. Wynikowe aplikacje zazwyczaj mają prawie tak samo samo jak ręcznie napisaną wersję.

  Jeśli jednak zaczniesz od istniejącej aplikacji, może się okazać, że wiele refaktoryzacji jest wymaganych do oddzielenia różnych zachowań, które podlegają modelowi, aby można je było niezależnie zmieniać. Zalecamy ocenę tego aspektu aplikacji podczas szacowania kosztów projektu.

## <a name="configuring-your-application-from-a-model"></a>Konfigurowanie aplikacji z modelu
 Jeśli chcesz różnić zachowanie aplikacji w czasie działania, nie możesz użyć generowania kodu, który generuje kod źródłowy przed skompilowanie aplikacji. Zamiast tego możesz zaprojektować aplikację tak, aby odczytywała model i odpowiednio zmieniała jego zachowanie. Aby uzyskać więcej informacji, zobacz:

- [Porady: otwieranie modelu z pliku w kodzie programu](../modeling/how-to-open-a-model-from-file-in-program-code.md)

  Tę metodę można również stosować przyrostowo, ale na początku jest więcej pracy. Należy napisać kod, który będzie odczytywać model, i skonfigurować platformę, która umożliwia dostęp do jego wartości dla części zmiennych. Tworzenie ogólnych części zmiennych jest droższe niż generowanie kodu.

  Aplikacja ogólna zazwyczaj wykonuje mniej dobrze niż jej określone odpowiedniki. Jeśli wydajność ma kluczowe znaczenie, plan projektu powinien obejmować ocenę tego ryzyka.

## <a name="developing-a-derived-application"></a>Tworzenie aplikacji pochodnej
 Przydatne mogą być następujące ogólne wskazówki.

- **Rozpocznij określone, a następnie uogólnij.** Najpierw napisz określoną wersję aplikacji. Ta wersja powinna działać w jednym zestawie warunków. Gdy wszystko będzie działać prawidłowo, możesz sprawić, że część z nich będzie pochodzić z modelu. Stopniowo rozszerzaj pochodne części.

     Na przykład przed zaprojektowaną aplikacją internetową, która przedstawia strony zdefiniowane w modelu, zaprojektuj witrynę internetową, która ma określony zestaw stron internetowych.

- **Modelowanie aspektów wariantów.** Zidentyfikuj aspekty, które będą się różnić, między jednym wdrożeniem a innym lub w czasie, w zależności od zmian wymagań. Są to aspekty, które powinny pochodzić z modelu.

     Jeśli na przykład zestaw stron internetowych i linki między nimi się zmienią, ale styl i format stron są zawsze takie same, model powinien opisywać linki, ale nie musi opisywać formatu stron.

- **Oddzielne kwestie.** Jeśli aspekty zmiennych można podzielić na niezależne obszary, użyj oddzielnych modeli dla każdego obszaru. Za pomocą modeluBus można zdefiniować operacje, które mają wpływ zarówno na modele, jak i ograniczenia między nimi.

     Na przykład użyj jednego modelu, aby zdefiniować nawigację między stronami internetowymi i innym modelem w celu zdefiniowania układu stron.

- **Modelowanie wymagania, a nie rozwiązania.** Zaprojektuj model tak, aby opisuje wymagania użytkownika. Z kolei notacja nie jest projektowana zgodnie ze zmiennymi aspektami implementacji.

     Na przykład model nawigacji internetowej powinien reprezentować strony internetowe i hiperlinki między nimi. Model nawigacji internetowej nie powinien reprezentować fragmentów kodu HTML ani klas w aplikacji.

- **Generować lub interpretować?** Jeśli wymagania dotyczące określonego wdrożenia rzadko zmienią się, wygeneruj kod programu z modelu. Jeśli wymagania mogą często ulec zmianie lub mogą istnieć w więcej niż jednym wariancie w tym samym wdrożeniu, napisz aplikację, aby mogła odczytywać i interpretować model.

     Jeśli na przykład używasz modelu witryny sieci Web do opracowywania serii różnych i oddzielnie zainstalowanych witryn internetowych, należy wygenerować kod witryny na podstawie modelu. Jednak używasz modelu do kontrolowania witryny, która zmienia się każdego dnia, lepiej jest napisać serwer internetowy, który odczytuje model i odpowiednio prezentuje witrynę.

- **UML czy DSL?** Rozważ utworzenie notacji modelowania przy użyciu stereotypów w celu rozszerzenia UML. Zdefiniuj DSL, jeśli nie ma diagramu UML, który pasuje do tego celu. Należy jednak unikać łamania standardowej semantyki UML.

     Na przykład diagram klas UML jest kolekcją pól i strzałek; za pomocą tej notacji teoretycznie można zdefiniować wszystko. Nie zalecamy jednak używania diagramu klas z wyjątkiem sytuacji, w której w rzeczywistości opisujesz zestaw typów. Można na przykład dostosować diagramy klas, aby opisać różne typy stron internetowych.

## <a name="see-also"></a>Zobacz też

- [Generowanie kodu z języka specyficznego dla domeny](../modeling/generating-code-from-a-domain-specific-language.md)
- [Porady: otwieranie modelu z pliku w kodzie programu](../modeling/how-to-open-a-model-from-file-in-program-code.md)
- [Generowanie kodu czasu projektowania przy użyciu szablonów tekstowych T4](../modeling/design-time-code-generation-by-using-t4-text-templates.md)
