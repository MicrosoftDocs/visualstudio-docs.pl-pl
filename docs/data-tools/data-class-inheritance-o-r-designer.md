---
title: Dziedziczenie klas danych (Projektant O-R)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: af32653c-f4e6-4217-8c5a-e32b322b4918
author: gewarren
ms.author: gewarren
manager: douge
ms.prod: visual-studio-dev15
ms.workload:
- data-storage
ms.openlocfilehash: e554561598086193b4862f5962435b25a1ae4d47
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53935765"
---
# <a name="data-class-inheritance-or-designer"></a>Dziedziczenie klas danych (O/R Designer)

Podobnie jak inne obiekty można użyć dziedziczenia klasy LINQ do SQL i mogą pochodzić z innych klas. W kodzie można określić relacji dziedziczenia między obiektami, deklarując, że jedna klasa dziedziczy z innego. W bazie danych relacje dziedziczenia są tworzone na kilka sposobów. **Object Relational Designer** (**O/R Designer**) obsługuje dziedziczenia pojedynczej tabeli, co jest często stosowana w systemach relacyjnych.

Dziedziczenie pojedynczej tabeli Brak tabeli pojedynczej bazy danych, która zawiera kolumny dla klas podstawowych i pochodnych. Z danymi relacyjnymi kolumna dyskryminatora zawiera wartość, która określa, która z klas należą wszelkie podane rekordy do. Na przykład, rozważmy `Persons` tabelę, która zawiera wszystkich stosowanych przez firmę. Niektórzy użytkownicy są pracownicy i niektóre osoby menedżerów. `Persons` Tabela zawiera kolumnę o nazwie `Type` zawierający wartość 1 dla menedżerów i wartość 2 dla pracowników. `Type` Kolumna jest kolumną dyskryminatora. W tym scenariuszu możesz utworzyć podklasę pracowników i wypełnić klasy za pomocą tylko te rekordy, które mają `Type` wartość 2.

Po skonfigurowaniu dziedziczenia klas jednostek za pomocą [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)], przeciągnij pojedynczej tabeli, która zawiera dane dziedziczenia w Projektancie dwa razy: jeden raz dla każdej klasy w hierarchii dziedziczenia. Po dodaniu tabel do projektanta, łącz je z elementem dziedziczenia z **Object Relational Designer** przybornika, a następnie ustaw cztery właściwości dziedziczenia w **właściwości** okna.

## <a name="inheritance-properties"></a>Dziedziczenie właściwości

W poniższej tabeli wymieniono właściwości dziedziczenia i ich opisy:

|Właściwość|Opis|
|--------------|-----------------|
|**Właściwość rozróżniacza**|Właściwość (mapowane na kolumny), która określa, która klasa należy bieżący rekord.|
|**Wartość dyskryminatora klasy bazowej**|Wartość (w kolumnie wyznaczony jako **właściwość rozróżniacza**) określający, czy rekord ma klasę bazową.|
|**Wartość dyskryminatora klasy pochodnej**|Wartość (WE właściwości wyznaczony jako **właściwość rozróżniacza**) określający, czy rekord jest klasy pochodnej.|
|**Wartość domyślna dziedziczenia**|Klasa, która jest wypełniana podczas wartości właściwości są oznaczone jako **właściwość rozróżniacza** nie pasują do jednego **wartość dyskryminatora klasy podstawowej** lub **klasy pochodnej Wartość dyskryminatora**.|

Tworzenie modelu obiektów, która korzysta z dziedziczenia i odpowiada relacyjnej bazie danych może być nieco mylące. Ten temat zawiera informacje o podstawowych pojęć i poszczególne właściwości, które są wymagane do skonfigurowania dziedziczenia. W poniższych tematach przedstawiono bardziej zrozumiały opis sposobu konfigurowania dziedziczenia z **O/R Designer**.

|Temat|Opis|
|-----------|-----------------|
|[Instrukcje: Skonfigurować dziedziczenie za pomocą Projektanta obiektów relacyjnych](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|W tym artykule opisano sposób konfigurowania klas jednostek, korzystających z pojedynczej tabeli dziedziczenia przy użyciu **O/R Designer**.|
|[Przewodnik: Tworzenie zapytań LINQ do klas SQL za pomocą pojedynczej tabeli dziedziczenia (O/R Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|Zawiera instrukcje krok po kroku dotyczące sposobu konfigurowania klas jednostek, korzystających z pojedynczej tabeli dziedziczenia przy użyciu **O/R Designer**.|

## <a name="see-also"></a>Zobacz także

- [Narzędzi LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Przewodnik: Tworzenie zapytań LINQ do klas SQL (Projektant O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Przewodnik: Tworzenie zapytań LINQ do klas SQL za pomocą pojedynczej tabeli dziedziczenia (O/R Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [Wprowadzenie](/dotnet/framework/data/adonet/sql/linq/getting-started)