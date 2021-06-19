---
title: Języki specyficzne dla domeny — informacje
description: Dowiedz się, jak język specyficzny dla domeny (DSL) jest przeznaczony do wyrażania instrukcji w określonej przestrzeni problemu lub domenie.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: ab56292aafda25efc0b3dfeeb14e93d4502a5567
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112384983"
---
# <a name="about-domain-specific-languages"></a>Języki specyficzne dla domeny — informacje

W przeciwieństwie do języka ogólnego przeznaczenia, takiego jak C# lub UML, język specyficzny dla domeny (DSL) jest przeznaczony do wyrażania instrukcji w określonej przestrzeni problemu lub domenie.

Dobrze znane listy DSL obejmują wyrażenia regularne i język SQL. Każdy JĘZYK DSL jest znacznie lepszy niż język ogólnego przeznaczenia do opisywania operacji na ciągach tekstowych lub bazie danych, ale znacznie gorszy w przypadku opisywania koncepcji, które znajdują się poza własnym zakresem. Poszczególne branże mają również własne adresy DSL. Na przykład w branży telekomunikacyjnej języki opisu połączeń są powszechnie używane do określania sekwencji stanów w rozmowach telefonicznych, a w branży podróży telekomunikacyjnych standardowy język DSL jest używany do opisywania rezerwacji lotów.

Twoja firma i Twój projekt mają również do czynienia ze specjalnymi zestawami koncepcji, które można opisać za pomocą DSL. Na przykład można zdefiniować DSL dla jednej z tych aplikacji:

- Planowanie ścieżek nawigacji w witrynie internetowej.

- Diagramy okablowania dla składników elektronicznych.

- Sieci przenośników taśmowych i ładunek do obsługi sprzętu dla lotniska.

Podczas projektowania DSL, należy  zdefiniować klasę domeny dla każdego z ważnych pojęć w domenie, takich jak strony sieci Web, lamp lub punktu zaewidencji lotniska. Aby połączyć *te koncepcje,* należy zdefiniować relacje domeny, takie jak hiperlink, przewodowy lub przenośnik taśmowy.

Użytkownicy DSL utworzyć *modele.* Modele są *wystąpieniami* DSL. Opisują one na przykład określoną witrynę internetową, okablowanie określonego urządzenia lub system obsługi poszczególnych lotniska.

Użytkownicy mogą wyświetlać model jako diagram lub jako formularz systemu Windows. Modele można również wyświetlać w formacie XML, czyli w jaki sposób są przechowywane. Podczas definiowania DSL, należy zdefiniować sposób wystąpień każdej klasy domeny i relacji na ekranie użytkownika. Typowy DSL jest wyświetlany jako kolekcja ikon lub prostokątów połączonych strzałkami.

Na poniższej ilustracji przedstawiono mały model w diagramie DSL:

![Tudor Family Tree Model](../modeling/media/tudor_familytreemodel.png)

## <a name="what-you-can-do-with-dsls"></a>Co można zrobić za pomocą plików DSL

Typowym zastosowaniem DSL jest generowanie kodu programu lub innych artefaktów. Podczas definiowania DSL, można zdefiniować szablony *tekstowe,* które odczytują model DSL i generują pliki tekstowe.

Można na przykład napisać szablony, które wygenerują część oprogramowania do obsługi lotniska, a także niektóre dokumenty użytkowników opisujące plan.

Po zdefiniować DSL, można rozpowszechniać go do innych użytkowników, którzy mogą zainstalować go na własnych komputerach. Użytkownicy DSL można tworzyć i edytować modele w Visual Studio.

Można również zdefiniować polecenia menu i inne narzędzia, które ułatwiają użytkownikom edytowanie DSL, ograniczenia weryfikacji, aby upewnić się, że DSL jest używany prawidłowo i szablony elementów, które ułatwiają użytkownikom tworzenie nowych wystąpień. Można opakowane co najmniej jeden plik DSL za pomocą jego narzędzi i innych rozszerzeń Visual Studio jako zintegrowany pakiet.

Zazwyczaj język specyficzny dla domeny jest tworzony, gdy zespół programistów musi napisać podobny kod dla kilku produktów. Na przykład firma, która specjalizuje się w systemach obsługi plików, może zdefiniować ścieżkę DSL, z której może wygenerować część kodu dla każdej instalacji. Zalety DSL są zrozumiałe dla ich klientów, że kod wygenerowany na jego podstawie jest niezawodny i że system może być szybko aktualizowany, jeśli wymagania klientów zmienią się.

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] Umożliwia utworzenie języka specyficznego dla domeny, który ma własnego projektanta graficznego i własną notację diagramu, a następnie użycie języka do wygenerowania odpowiedniego kodu źródłowego dla każdego projektu.

## <a name="domain-specific-development"></a>Domain-Specific tworzenia aplikacji

Opracowywanie specyficzne dla domeny to proces identyfikowania części aplikacji, które mogą być modelowane przy użyciu języka specyficznego dla domeny, a następnie konstruowania języka i wdrażania go dla deweloperów aplikacji. Deweloperzy używają języka specyficznego dla domeny do konstruowania modeli, które są specyficzne dla ich aplikacji, używają modeli do generowania kodu źródłowego, a następnie używają kodu źródłowego do tworzenia aplikacji.

## <a name="aspects-of-graphical-domain-specific-development"></a>Aspekty projektowania graficznego Domain-Specific graficznego

Graficzny język specyficzny dla domeny musi zawierać następujące funkcje:

- Notacja

- Model domeny

- Generowanie artefaktów

- Serializacja

- Integracja z programem Visual Studio

### <a name="notation"></a>Notacja

Język specyficzny dla domeny musi mieć względnie niewielki zestaw elementów, które można łatwo zdefiniować i rozszerzyć w celu reprezentowania konstrukcji specyficznych dla domeny. Notacja składa się z kształtów, które reprezentują elementy, i łączników, które reprezentują relacje między elementami, na powierzchni diagramu graficznego. W programie kształty można rozszerzać i udoskonalać w celu [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] reprezentowania elementów języka specyficznego dla domeny.

### <a name="domain-model"></a>Model domeny

Język specyficzny dla domeny musi łączyć zestaw elementów i relacje między nimi w spójną gramatykę. Musi również definiować, czy kombinacje elementów i relacji są prawidłowe. Na przykład języki programowania zwykle uniemożliwiają dziedziczenie cykliczne, w którym jedna klasa jest pochodną drugiej klasy, a druga klasa jest pochodną pierwszej klasy. Ograniczenia mogą być również używane do wyrażania logiki biznesowej, na przykład jedna osoba nie może być zależna od siebie. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] używa ograniczeń do wyrażania rodzajów ograniczeń, których wymaga większość języków specyficznych dla domeny.

### <a name="artifact-generation"></a>Generowanie artefaktów

Jednym z głównych celów języka specyficznego dla domeny jest wygenerowanie artefaktu, na przykład kodu źródłowego, pliku XML lub innych danych, których można użyć. Zazwyczaj zmiana w modelu oznacza zmianę artefaktu. Za pomocą funkcji [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] można generować artefakty i generować je ponownie po zmianie modelu.

### <a name="serialization"></a>Serializacja

Język specyficzny dla domeny musi być utrwalony w określonej postaci, która może być edytowana, zapisywana, zamykana i ponownie ładowana. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] używa formatu XML, który umożliwia definiowanie i dostosowywanie sposobu serializacji lub utrwalania języka specyficznego dla domeny.

### <a name="integration-with-visual-studio"></a>Integracja z programem Visual Studio

Ponieważ [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] usługa jest hostowana Visual Studio, rozszerza wiele okien Visual Studio kontrolek. Umożliwia również dostosowywanie zachowania poleceń menu, elementów przybornika i innych elementów interfejsu użytkownika.

Można również utworzyć adapter magistrali modelu dla języka specyficznego dla domeny. Ta karta pozwala odwoływać się do modelu i elementów w modelu oraz umożliwia pisanie kodu, który może uzyskać dostęp do wystąpienia DSL i zaktualizować je. Za pomocą zaawansowanego mechanizmu magistrali modeli można pisać rozszerzenia Visual Studio, które działają z wieloma modelami. Można również pisać aplikacje autonomiczne, które działają z modelami. Aby uzyskać więcej informacji, zobacz [Integrating Models by using Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md)(Integrowanie modeli przy użyciu Visual Studio Modelbus).

## <a name="benefits-of-domain-specific-development"></a>Zalety Domain-Specific dewelopera

Język specyficzny dla domeny może zapewnić następujące korzyści:

- Zawiera konstrukcje, które dokładnie pasują do obszaru problemu.

     W przeciwieństwie do języków ogólnego przeznaczenia język specyficzny dla domeny składa się z elementów i relacji, które bezpośrednio reprezentują logikę obszaru problemów. Na przykład aplikacja ubezpieczenia musi zawierać elementy zasad i roszczeń. Język specyficzny dla domeny ułatwia projektowanie aplikacji oraz znajdowanie i korygowanie błędów logiki.

- Umożliwia użytkownikom niebędącym deweloperami i osobom, które nie znają domeny, zrozumienie ogólnego projektu.

     Za pomocą graficznego języka specyficznego dla domeny można utworzyć wizualną reprezentację domeny, aby deweloperzy niebędący deweloperami w stanie łatwo zrozumieć projekt aplikacji.

- Ułatwia tworzenie prototypu końcowej aplikacji.

     Deweloperzy mogą używać kodu generowanego przez model w celu utworzenia prototypowej aplikacji, która może być pokazywana klientom.

## <a name="the-process-of-domain-specific-development"></a>Proces tworzenia Domain-Specific aplikacji

Większość zespołów programistów, które używają języków specyficznych dla domeny, wykonaj następujące kroki, aby utworzyć i używać swoich modeli:

- Zespół rozróżnia zmienne części domeny od części, które nigdy się nie zmieniają.

- Deweloperzy piszą kod dla stałych części i pozostawiają punkty rozszerzenia dla części zmiennych.

- Główny deweloper oprogramowania lub architekt tworzy język specyficzny dla domeny, który zawiera wzorce projektowe stałych części domeny i punktów rozszerzenia dla części zmiennych.

- Główny deweloper oprogramowania lub architekt wdraża język specyficzny dla domeny dla deweloperów różnych aplikacji, które tworzy zespół.

- Każdy deweloper tworzy model, który ma zastosowanie do określonej aplikacji.
