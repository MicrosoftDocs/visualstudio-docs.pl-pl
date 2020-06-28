---
title: Dziedziczenie klasy danych (Projektant O-R)
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: af32653c-f4e6-4217-8c5a-e32b322b4918
author: ghogen
ms.author: ghogen
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 7172c868780aec61de8688614fbb93627dc23bf5
ms.sourcegitcommit: 66f31cc4ce1236e638ab58d2f70d3646206386fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/27/2020
ms.locfileid: "85462398"
---
# <a name="data-class-inheritance-or-designer"></a>Dziedziczenie klas danych (Object Relational Designer)

Podobnie jak w przypadku innych obiektów, klasy LINQ to SQL mogą używać dziedziczenia i pochodzić z innych klas. W kodzie można określić relacje dziedziczenia między obiektami przez zadeklarowanie, że jedna klasa dziedziczy z innej. W bazie danych relacje dziedziczenia są tworzone na kilka sposobów. **Object Relational Designer** (**Projektant O/R**) wspiera koncepcję dziedziczenia pojedynczej tabeli, ponieważ jest ona często zaimplementowana w systemach relacyjnych.

W przypadku dziedziczenia z jedną tabelą istnieje pojedyncza tabela bazy danych zawierająca kolumny dla klas podstawowych i pochodnych. W przypadku danych relacyjnych kolumna rozróżniacza zawiera wartość określającą, do której klasy należy dany rekord. Rozważmy na przykład `Persons` tabelę zawierającą wszystkie osoby zaangażowane przez firmę. Niektóre osoby to pracownicy i niektórzy ludzie są kierownikami. `Persons`Tabela zawiera kolumnę o nazwie `Type` , która ma wartość 1 dla menedżerów i wartość 2 dla pracowników. `Type`Kolumna jest kolumną rozróżniacza. W tym scenariuszu można utworzyć podklasę pracowników i wypełnić klasę tylko rekordami o `Type` wartości 2.

Konfigurując dziedziczenie w klasach jednostek przy użyciu [!INCLUDE[vs_ordesigner_short](../data-tools/includes/vs_ordesigner_short_md.md)] , przeciągnij pojedynczą tabelę zawierającą dane dziedziczenia do projektanta dwa razy: jeden raz dla każdej klasy w hierarchii dziedziczenia. Po dodaniu tabel do projektanta, połącz je z elementem dziedziczenia z przybornika **Object Relational Designer** , a następnie ustaw cztery właściwości dziedziczenia w oknie **Właściwości** .

## <a name="inheritance-properties"></a>Właściwości dziedziczenia

W poniższej tabeli wymieniono właściwości dziedziczenia i ich opisy:

|Właściwość|Opis|
|--------------|-----------------|
|**Właściwość rozróżniacza**|Właściwość (zamapowana na kolumnę), która określa, do której klasy należy bieżący rekord.|
|**Wartość rozróżniacza klasy bazowej**|Wartość (w kolumnie wyznaczono jako **Właściwość dyskryminatora**), która określa, że rekord jest klasą bazową.|
|**Wartość rozróżniacza klasy pochodnej**|Wartość (we właściwości wyznaczonej jako **właściwość rozróżniacza**), która określa, że rekord jest klasą pochodną.|
|**Domyślne dziedziczenie**|Klasa, która jest wypełniana, gdy wartość we właściwości wyznaczonej jako **właściwość rozróżniacza** nie pasuje do **wartości rozróżniacza klasy bazowej** lub **wartości rozróżniacza klasy pochodnej**.|

Tworzenie modelu obiektów, który używa dziedziczenia i odpowiada danych relacyjnych, może być nieco mylące. Ten temat zawiera informacje o podstawowych pojęciach i poszczególnych właściwościach, które są wymagane do skonfigurowania dziedziczenia. Poniższe tematy zawierają wyraźniejsze wyjaśnienie sposobu konfigurowania dziedziczenia przy użyciu **projektanta o/R**.

|Temat|Opis|
|-----------|-----------------|
|[Instrukcje: konfigurowanie dziedziczenia za pomocą narzędzia Object Relational Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|Opisuje sposób konfigurowania klas jednostek, które używają dziedziczenia pojedynczej tabeli przy użyciu **projektanta o/R**.|
|[Przewodnik: tworzenie klas LINQ to SQL przy użyciu dziedziczenia pojedynczej tabeli (Projektant O/R)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|Zawiera instrukcje krok po kroku dotyczące konfigurowania klas jednostek, które używają dziedziczenia pojedynczej tabeli przy użyciu **projektanta o/R**.|

## <a name="see-also"></a>Zobacz też

- [Narzędzia LINQ to SQL w programie Visual Studio](../data-tools/linq-to-sql-tools-in-visual-studio2.md)
- [Przewodnik: tworzenie klas LINQ to SQL (Projektant O-R)](how-to-create-linq-to-sql-classes-mapped-to-tables-and-views-o-r-designer.md)
- [Przewodnik: tworzenie klas LINQ to SQL przy użyciu dziedziczenia pojedynczej tabeli (Projektant O/R)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)
- [Wprowadzenie](/dotnet/framework/data/adonet/sql/linq/getting-started)