---
title: Wybieranie szablonu rozwiązania dotyczącego języka specyficznego dla domeny
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, solution templates
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 6b3e6d9812f06df6d4af65f624579ec5f6550515
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55913317"
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>Wybieranie szablonu rozwiązania dotyczącego języka specyficznego dla domeny
Aby utworzyć rozwiązanie języka dotyczącego określonej domeny, wybierz jedną z szablonów rozwiązań, które są dostępne w Kreatorze projektanta języka specyficznego dla domeny. Wybierając szablon, który najbardziej przypomina język, który ma zostać utworzona, można zminimalizować modyfikacjach, które należy podjąć, począwszy od rozwiązania.

 Następujące szablony rozwiązań są dostępne w Kreatorze projektanta języka specyficznego dla domeny.

|Szablon|Funkcje|Opis|
|-|-|-|
|Diagramy klas|-Kształtów przedziałów<br />— Dziedziczenie klasa<br />-Relacji dziedziczenia<br />-Kształt dziedziczenia<br />— Właściwości relacji|Użyj tego szablonu rozwiązania, jeśli zawiera języka specyficznego dla domeny, jednostki i relacje, które mają właściwości. Ten szablon umożliwia utworzenie języka specyficznego dla domeny, podobny diagramów klas UML. Obiekty główne są klasy i interfejsy, wraz z relacji skojarzenia, generalizacji i wdrażanie. Klasy lub interfejsu jest wyświetlany jako okno, który zawiera listę atrybutów.|
|Diagramy składników|— Porty|Użyj tego szablonu rozwiązania, jeśli języka specyficznego dla domeny obejmuje składniki, czyli części systemu oprogramowania. Ten szablon umożliwia utworzenie języka specyficznego dla domeny, który przypomina diagramy składników UML. Obiekty główne są składniki i portów, które są wyświetlane jako małe kształty na zewnątrz składników.|
|Diagramy przepływu zadań|— Obrazów i kształtów geometrycznych<br />-   *Swimlanes*|Użyj tego szablonu rozwiązania, jeśli języka specyficznego dla domeny zawiera przepływy pracy, Państwa lub sekwencji. Ten szablon umożliwia utworzenie języka specyficznego dla domeny, który przypomina diagramy aktywności UML. Jednostki głównej jest działaniem, a relacji głównego jest przejście między działaniami. Szablon zawiera kilka innych elementów, takich jak stan początkowy stan końcowy i pasek synchronizacji.|
|Minimalny języka|-Jedną klasę i kształt<br />-Jednej relacji i łącznik|Użyj tego szablonu rozwiązania, jeśli języka specyficznego dla domeny wygląda inaczej niż inne szablony. Ten szablon umożliwia utworzenie języka specyficznego dla domeny, który ma dwie klasy i jedna relacja, które są reprezentowane w **przybornika** jako **pole** i **wiersza**. Klasa, jak i relacji ma przykład właściwość ciągu.|
|Minimalny projektanta formularza systemu Windows|-Małe model.<br />-Windows formularz, który wyświetla model.|Użyj tego szablonu, aby skompilować aplikację, w którym DSL jest powiązany z formularzem Windows, a nie graficznego projektanta.<br /><br /> Formularz, który działa jako interfejs użytkownika dla języka znajduje się w folderze Dsl\UI.<br /><br /> Należy skompilować projekt przed otwarciem projektanta formularzy.<br /><br /> Aby uzyskać więcej informacji, zobacz [Tworzenie języka specyficznego dla domeny Windows Forms-Based](../modeling/creating-a-windows-forms-based-domain-specific-language.md).|
|Projektant WPF minimalny|-Małe modelu<br />— Windows Presentation Foundation interfejs użytkownika, który wyświetla model|Użyj tego szablonu, aby skompilować aplikację, w którym DSL jest powiązany z interfejsem użytkownika WPF, a nie graficznego projektanta.<br /><br /> Projektant interfejsu użytkownika znajduje się w folderze Dsl\UI.<br /><br /> Należy skompilować projekt przed otwarciem projektanta interfejsu użytkownika.<br /><br /> Aby uzyskać więcej informacji, zobacz [Tworzenie języka specyficznego dla domeny WPF-Based](../modeling/creating-a-wpf-based-domain-specific-language.md).|
|Biblioteka DSL|— Biblioteka minimalny|Użyj tego szablonu, jeśli chcesz skompilować częściową definicję DSL, który można zaimportować do innych definicji DSL.|

## <a name="see-also"></a>Zobacz też

- [Przegląd narzędzi języka specyficznego dla domeny](../modeling/overview-of-domain-specific-language-tools.md)
