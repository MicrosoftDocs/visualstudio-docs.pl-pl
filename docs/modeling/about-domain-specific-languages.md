---
title: Języki specyficzne dla domeny — informacje
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4684a0256e01cafe79fc90ae1ae97dfc2be047d6
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62823365"
---
# <a name="about-domain-specific-languages"></a>Języki specyficzne dla domeny — informacje

W przeciwieństwie do języka ogólnego przeznaczenia, takich jak C# lub UML języka specyficznego dla domeny (DSL) jest przeznaczona do express instrukcji w konkretnych problemów miejsca lub domenie.

Dobrze znanych języków DSL obejmują wyrażeń regularnych i SQL. Każdy język DSL jest znacznie wyższa niż uniwersalny język opisu operacji na ciągi tekstowe lub bazy danych, ale znacznie gorsza do opisywania pojęcia, które wykraczają poza zakres swój własny. Poszczególnych branż mają również własne językami DSL. Na przykład w branży usług telekomunikacyjnych, wywołaj opis języki są powszechnie używane do określ stanów połączeń telefonicznych i w powietrzu podróży w branży standard, używane do opisywania Rezerwacje lotów DSL.

Firmy, a projekt także dotyczyć specjalne rodzaje pojęcia, które można opisać za pomocą języka DSL. Na przykład można zdefiniować DSL dla jednego z tych aplikacji:

- Plan ścieżki nawigacji w witrynie sieci Web.

- Diagramy połączeń dla komponentów elektronicznych.

- Sieci taśmy przenoszące i obsługi sprzętu na lotnisku bagażu.

Podczas projektowania DSL, należy zdefiniować *klasy domeny* dla każdego ważnych pojęć w domenie, np. strony sieci web, lamp lub port lotniczy biurku ewidencjonowania. Należy zdefiniować *relacje domeny* takie jak hiperłącza, o komunikacji sieciowej lub pas taśmy połączyć ze sobą pojęcia.

Tworzenie użytkowników DSL *modeli.* Modele są *wystąpień* z język DSL. Na przykład opisują one określonej witryny internetowej lub okablowanie określonego urządzenia lub bagażu systemu w określonym porcie lotniczym obsługi.

Użytkownicy mogą wyświetlać modelu jako diagramu lub formularza Windows. Modele można również wyświetlać jako kod XML, który jest, jak są one przechowywane. Podczas definiowania DSL, należy zdefiniować jak wystąpień każdej klasy domeny i relacje są pokazywane na ekranie użytkownika. Typowe DSL jest wyświetlany jako kolekcja ikon lub prostokąty połączone przez strzałki.

Na poniższej ilustracji przedstawiono model małych w DSL diagramu:

![Model drzewa rodziny Tudorów](../modeling/media/tudor_familytreemodel.png)

## <a name="what-you-can-do-with-dsls"></a>Co można zrobić za pomocą języków DSL

Typowa aplikacja języka DSL ma generować kod programu lub inne artefakty. Podczas definiowania DSL można zdefiniować *szablonów tekstowych* , odczytywanie modelu DSL i generowanie plików tekstowych.

Na przykład można napisać Szablony używające plan lotniska i generować część oprogramowania bagażu obsługi, a także niektóre dokumenty użytkowników, które opisują planu.

Po zdefiniowaniu DSL można rozdystrybuować innym użytkownikom, którzy można zainstalować na swoich komputerach. Użytkownicy DSL można tworzyć i edytować modele w programie Visual Studio.

Można również zdefiniować polecenia menu i innych narzędzi, które pomagają użytkownikom edytowanie DSL, ograniczenia sprawdzania poprawności, aby mieć pewność, że język DSL są prawidłowo wykorzystywane i szablonów elementów, które pomagają użytkownikom tworzenie nowych wystąpień. Co najmniej jeden językami DSL za pomocą swoich narzędzi i inne rozszerzenia programu Visual Studio można opakować jako pakiet zintegrowanego.

Zazwyczaj języka specyficznego dla domeny jest tworzone, gdy zespół programistyczny musi napisać kod podobny dla wielu produktów. Na przykład firma, która specjalizuje się w bagażu Obsługa systemów może zdefiniować bagażu DSL śledzenie, z którego mogą wygenerować niektóre z kodu dla każdej instalacji. Zalety język DSL są, czy go może być rozumiany przez klientów, czy kodu wygenerowanego na podstawie jego jest niezawodne i że można szybko zaktualizować system jeśli zmienią się wymagania klientów.

[!INCLUDE[dsl](../modeling/includes/dsl_md.md)] Umożliwia tworzenie języka specyficznego dla domeny, który ma graficznego projektanta i własnych notacji diagramu, a następnie użyj języka do wygenerowania odpowiedniego kodu źródłowego dla każdego projektu.

## <a name="domain-specific-development"></a>Programowanie specyficznego dla domeny

Programowanie specyficznego dla domeny to proces identyfikowania części aplikacji, które mogą być modelowane przy użyciu języka specyficznego dla domeny, a następnie tworząc języka i wdrażania dla deweloperów aplikacji. Deweloperzy używają języka specyficznego dla domeny do tworzenia modeli, które są specyficzne dla aplikacji, użyj modele, aby wygenerować kod źródłowy, a następnie użyj kodu źródłowego do tworzenia aplikacji.

## <a name="aspects-of-graphical-domain-specific-development"></a>Aspekty graficznych programowania specyficznego dla domeny

Graficzny języka specyficznego dla domeny należy uwzględnić następujące funkcje:

- Notacja

- Model domeny

- Generowanie artefaktu

- Serializacja

- Integracja z programem Visual Studio

### <a name="notation"></a>Notacja

Języka specyficznego dla domeny musi mieć rozsądnie małe rozmiary zestaw elementów, które można łatwo definiować i rozszerzone do reprezentowania konstrukcje specyficznego dla domeny. Notacja składa się z kształtów, które reprezentują elementy, i łączników, które reprezentują relacje między elementami na powierzchni diagramu graficznego. W [!INCLUDE[dsl](../modeling/includes/dsl_md.md)], kształty, można ją rozszerzać oraz, aby reprezentować elementy języka specyficznego dla domeny.

### <a name="domain-model"></a>Domain Model

Połączyć zbiór elementów i relacji między nimi do spójnego gramatyki języka specyficznego dla domeny. Należy także zdefiniować, czy kombinacji elementów i relacji są prawidłowe. Języki programowania uniemożliwiają zazwyczaj Dziedziczenie cykliczne, w którym jeden klasa pochodzi od klasy sekundę, a druga klasa pochodzi od pierwszej klasy. Ograniczenia mogą również wyrażanie logiki biznesowej, na przykład jedna osoba nie może być zależne od siebie. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] używa ograniczeń wyrażenia rodzaju ograniczenia, które wymagają większość języków specyficznych dla domeny.

### <a name="artifact-generation"></a>Generowanie artefaktu

Jednym z głównych celów języka specyficznego dla domeny jest generowanie artefakt, na przykład, kod źródłowy, plik XML lub inne użyteczne dane. Zazwyczaj zmiany w modelu oznacza zmianę w artefakcie. Możesz użyć [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] do generowania artefaktów i ponownie je wygenerować, po zmianie modelu.

### <a name="serialization"></a>Serializacja

Języka specyficznego dla domeny musi być utrwalone w jakiejś formy, która może być edytowany, zapisane, zamknięte i ponownie załadowany. [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] używa formacie XML, który umożliwia definiowanie i dostosowywanie jak języka specyficznego dla domeny jest serializowana, czy utrwalone.

### <a name="integration-with-visual-studio"></a>Integracja z programem Visual Studio

Ponieważ [!INCLUDE[dsl](../modeling/includes/dsl_md.md)] znajduje się w programie Visual Studio rozszerza wielu okna programu Visual Studio i formanty. Umożliwia on również dostosować zachowanie polecenia menu, elementy do przybornika i inne elementy interfejsu użytkownika.

Można również utworzyć kartę magistrali modelu dla danego języka specyficznego dla domeny. Ta karta umożliwia odwołanie do modelu i elementy wewnątrz modelu i umożliwia pisanie kodu, które mogą uzyskać dostęp i aktualizują wystąpienia język DSL. Za pomocą zaawansowanego mechanizmu Model Bus, można napisać rozszerzeń programu Visual Studio, współpracujących z wielu modeli. Możesz również zapisywać dane aplikacji autonomicznej, współpracujących z modeli. Aby uzyskać więcej informacji, zobacz [integrowanie modeli za pomocą programu Visual Studio Modelbus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).

## <a name="benefits-of-domain-specific-development"></a>Zalety tworzenia specyficznego dla domeny

Języka specyficznego dla domeny zapewnia następujące korzyści:

- Zawiera konstrukcje, które dokładnie dopasowywane problem.

     W przeciwieństwie do ogólnego przeznaczenia języków języka specyficznego dla domeny składa się z elementy i relacje, które reprezentują bezpośrednio logikę obszar problemu. Na przykład aplikacja ubezpieczenia mogą zawierać elementy zasad i oświadczeń. Domain-specific language ułatwia projektowanie aplikacji i Znajdź i usuń błędy logiki.

- Umożliwia osoby niebędące deweloperami i osoby, które nie znają domeny zrozumieć ogólny projekt.

     Za pomocą graficznego języka specyficznego dla domeny, można utworzyć wizualną reprezentację domeny, aby użytkownicy niebędący deweloperami, może łatwo zrozumieć projekt aplikacji.

- Ułatwia tworzenie prototypów końcowego aplikacji.

     Deweloperzy mogą używać kodu, który generuje ich modelu, do tworzenia aplikacji prototypu, które pokazują do klientów.

## <a name="the-process-of-domain-specific-development"></a>Proces tworzenia specyficznego dla domeny

Większość zespołów programistycznych korzystających z języków specyficznych dla domeny, wykonaj następujące kroki, tworzenie i używanie ich modeli:

- Zespół odróżnia zmiennej części domeny od elementów, które nigdy nie ulegną zmianie.

- Deweloperzy pisanie kodu dla części stały i pozostawić punktów rozszerzeń dla zmiennej części.

- Główny deweloper oprogramowania lub architekta tworzy uwzględniająca wzorce projektowe stałej części domeny oraz punkty rozszerzenia dla części zmiennej języka specyficznego dla domeny.

- Główny deweloper oprogramowania lub architekta wdraża deweloperzy różne aplikacje, które zespół tworzy języka specyficznego dla domeny.

- Każdy deweloper tworzy model, który ma zastosowanie do konkretnej aplikacji.