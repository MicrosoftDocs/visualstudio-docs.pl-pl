---
title: Dziedziczenie klasy danych (Projektant O-R) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
ms.assetid: af32653c-f4e6-4217-8c5a-e32b322b4918
caps.latest.revision: 7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 9e7dfc2b1137b30a03425f663d70e12c528dad39
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "72657412"
---
# <a name="data-class-inheritance-or-designer"></a>Dziedziczenie klas danych (Object Relational Designer)
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Podobnie jak w przypadku innych obiektów, [!INCLUDE[vbtecdlinq](../includes/vbtecdlinq-md.md)] klasy mogą używać dziedziczenia i pochodzić z innych klas. W kodzie można określić relacje dziedziczenia między obiektami przez zadeklarowanie, że jedna klasa dziedziczy z innej. W bazie danych relacje dziedziczenia są tworzone na kilka sposobów. [!INCLUDE[vs_ordesigner_long](../includes/vs-ordesigner-long-md.md)]( [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] ) Obsługuje koncepcję dziedziczenia pojedynczej tabeli, ponieważ jest ona często zaimplementowana w systemach relacyjnych.

 W przypadku dziedziczenia z jedną tabelą istnieje pojedyncza tabela bazy danych zawierająca kolumny dla klas podstawowych i pochodnych. W przypadku danych relacyjnych kolumna rozróżniacza zawiera wartość określającą, do której klasy należy dany rekord. Rozważmy na przykład tabelę osób, która zawiera wszystkich zatrudnionych przez firmę. Niektóre osoby to pracownicy i niektórzy ludzie są kierownikami. Tabela osoby zawiera kolumnę o nazwie Type o wartości 1 dla menedżerów i wartość 2 dla pracowników. Kolumna Type jest kolumną rozróżniacza. W tym scenariuszu można utworzyć podklasę pracowników i wypełnić klasę tylko rekordami o wartości typu 2.

 Konfigurując dziedziczenie w klasach jednostek przy użyciu [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] , przeciągnij pojedynczą tabelę zawierającą dane dziedziczenia do projektanta dwa razy: jeden raz dla każdej klasy w hierarchii dziedziczenia. Po dodaniu tabel do projektanta, połącz je z elementem dziedziczenia z przybornika **Object Relational Designer** , a następnie ustaw cztery właściwości dziedziczenia w oknie **Właściwości** .

## <a name="inheritance-properties"></a>Właściwości dziedziczenia
 W poniższej tabeli wymieniono właściwości dziedziczenia i ich opisy:

|Właściwość|Opis|
|--------------|-----------------|
|Właściwość rozróżniacza|Właściwość (zamapowana na kolumnę), która określa, do której klasy należy bieżący rekord.|
|Wartość rozróżniacza klasy bazowej|Wartość (w kolumnie wyznaczono jako właściwość dyskryminatora), która określa, że rekord jest klasą bazową.|
|Wartość rozróżniacza klasy pochodnej|Wartość (we właściwości wyznaczonej jako właściwość rozróżniacza), która określa, że rekord jest klasą pochodną.|
|Domyślne dziedziczenie|Klasa, która powinna zostać wypełniona, gdy wartość we właściwości wyznaczonej jako **właściwość rozróżniacza** nie pasuje do **wartości rozróżniacza klasy bazowej** lub **wartości rozróżniacza klasy pochodnej**.|

 Tworzenie modelu obiektów, który używa dziedziczenia i odpowiada danych relacyjnych, może być nieco mylące. Ten temat zawiera informacje o podstawowych pojęciach i poszczególnych właściwościach, które są wymagane do skonfigurowania dziedziczenia. Poniższe tematy zawierają wyraźniejsze wyjaśnienie sposobu konfigurowania dziedziczenia przy użyciu programu [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .

|Temat|Opis|
|-----------|-----------------|
|[Instrukcje: konfigurowanie dziedziczenia za pomocą narzędzia Object Relational Designer](../data-tools/how-to-configure-inheritance-by-using-the-o-r-designer.md)|Opisuje sposób konfigurowania klas jednostek, które używają dziedziczenia pojedynczej tabeli przy użyciu [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .|
|[Przewodnik: tworzenie klas LINQ do SQL za pomocą dziedziczenia pojedynczej tabeli (O/R Designer)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md)|Zawiera instrukcje krok po kroku dotyczące sposobu konfigurowania klas jednostek, które używają dziedziczenia pojedynczej tabeli przy użyciu [!INCLUDE[vs_ordesigner_short](../includes/vs-ordesigner-short-md.md)] .|

## <a name="see-also"></a>Zobacz też
 [Narzędzia LINQ to SQL w](../data-tools/linq-to-sql-tools-in-visual-studio2.md) przewodniku po programie Visual Studio [: tworzenie klas LINQ to SQL (Projektant o-r)](https://msdn.microsoft.com/library/35aad4a4-2e8a-46e2-ae09-5fbfd333c233) wskazówki [: tworzenie klas LINQ to SQL przy użyciu dziedziczenia pojedynczej tabeli (projektant o/r)](../data-tools/walkthrough-creating-linq-to-sql-classes-by-using-single-table-inheritance-o-r-designer.md) [wprowadzenie](https://msdn.microsoft.com/library/db8a557a-fef8-4f4f-bb91-8cff7250ee25)
