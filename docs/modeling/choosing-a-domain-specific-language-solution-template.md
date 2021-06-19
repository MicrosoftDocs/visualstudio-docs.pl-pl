---
title: Wybieranie szablonu rozwiązania dotyczącego języka specyficznego dla domeny
description: Dowiedz się, jak utworzyć rozwiązanie językowe specyficzne dla domeny, wybierając jeden z szablonów rozwiązań dostępnych w kreatorze projektanta języka Domain-Specific języka.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, solution templates
author: mgoertz-msft
ms.author: mgoertz
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: c1c638c5a45427fd474f085ff58c9d38682ee054
ms.sourcegitcommit: e3a364c014ccdada0860cc4930d428808e20d667
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/19/2021
ms.locfileid: "112385438"
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>Wybieranie szablonu rozwiązania dotyczącego języka specyficznego dla domeny
Aby utworzyć rozwiązanie językowe specyficzne dla domeny, wybierz jeden z szablonów rozwiązań dostępnych w Kreatorze projektanta języka Domain-Specific domeny. Wybierając szablon, który najlepiej przypomina język, który chcesz utworzyć, możesz zminimalizować modyfikacje, które należy wprowadzić w rozwiązaniu początkowym.

 Następujące szablony rozwiązań są dostępne w kreatorze Domain-Specific projektanta języka.

|Template|Funkcje|Opis|
|-|-|-|
|Diagramy klas|- Kształty przedziałów<br />- Dziedziczenie klas<br />- Dziedziczenie relacji<br />- Dziedziczenie kształtów<br />- Właściwości relacji|Użyj tego szablonu rozwiązania, jeśli język specyficzny dla domeny zawiera jednostki i relacje, które mają właściwości. Ten szablon tworzy język specyficzny dla domeny, który przypomina diagramy klas UML. Główne jednostki to klasy i interfejsy wraz z relacjami skojarzenia, uogólnienia i implementacji. Klasa lub interfejs jest wyświetlany jako pole zawierające listę atrybutów.|
|Diagramy składników|- Porty|Użyj tego szablonu rozwiązania, jeśli język specyficzny dla domeny zawiera składniki, czyli części systemu oprogramowania. Ten szablon tworzy język specyficzny dla domeny, który przypomina diagramy składników UML. Główne jednostki to składniki i porty, które są wyświetlane jako małe kształty na zewnątrz składników.|
|Diagramy przepływu zadań|— Kształty obrazów i geometrii<br />-   *Torów*|Użyj tego szablonu rozwiązania, jeśli język specyficzny dla domeny zawiera przepływy pracy, stany lub sekwencje. Ten szablon tworzy język specyficzny dla domeny, który przypomina diagramy aktywności UML. Jednostka główna to działanie, a główna relacja to przejście między działaniami. Szablon zawiera kilka innych elementów, takich jak stan rozpoczęcia, stan końcowy i pasek synchronizacji.|
|Minimalny język|- Jedna klasa i kształt<br />— Jedna relacja i łącznik|Użyj tego szablonu rozwiązania, jeśli język specyficzny dla domeny nie przypomina innych szablonów. Ten szablon tworzy język specyficzny dla domeny, który ma dwie klasy i jedną relację, która jest reprezentowana w **przyborniku** **jako** pole i **wiersz**. Każda klasa i relacja mają przykładową właściwość ciągu.|
|Minimal WinForm Designer|— Mały model.<br />— Formularz systemu Windows, który wyświetla model.|Użyj tego szablonu, jeśli chcesz utworzyć aplikację, w której DSL jest powiązany z formularzem systemu Windows, a nie projektantem graficznym.<br /><br /> Formularz, który działa jako interfejs użytkownika dla języka, znajduje się w folderze Dsl\UI.<br /><br /> Projekt należy skompilować przed otwarciem projektanta formularzy.<br /><br /> Aby uzyskać więcej informacji, zobacz Creating a Windows Forms-Based Domain-Specific Language (Tworzenie języka [Forms-Based Domain-Specific Windows).](../modeling/creating-a-windows-forms-based-domain-specific-language.md)|
|Minimal WPF Designer|— Mały model<br />— Windows Presentation Foundation interfejsu użytkownika, który wyświetla model|Użyj tego szablonu, jeśli chcesz utworzyć aplikację, w której DSL jest powiązany z interfejsem użytkownika WPF, a nie projektantem graficznym.<br /><br /> Projektant interfejsu użytkownika znajduje się w folderze Dsl\UI.<br /><br /> Należy skompilować projekt przed otwarciem projektanta interfejsu użytkownika.<br /><br /> Aby uzyskać więcej informacji, zobacz [Creating a WPF-Based Domain-Specific Language (Tworzenie WPF-Based Domain-Specific języku ).](../modeling/creating-a-wpf-based-domain-specific-language.md)|
|Biblioteka DSL|— Minimalna biblioteka|Użyj tego szablonu, jeśli chcesz utworzyć częściową definicję DSL, którą można zaimportować do innych definicji DSL.|

## <a name="see-also"></a>Zobacz też

- [Przegląd narzędzi języka specyficznego dla domeny](../modeling/overview-of-domain-specific-language-tools.md)
