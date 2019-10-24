---
title: Wybieranie szablonu rozwiązania dotyczącego języka specyficznego dla domeny
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, solution templates
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 110d357bd113913ab73990b8e3cfa12e4dd1cdae
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748522"
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>Wybieranie szablonu rozwiązania dotyczącego języka specyficznego dla domeny
Aby utworzyć rozwiązanie dla języka specyficznego dla domeny, wybierz jeden z szablonów rozwiązań dostępnych w Kreatorze projektant języka specyficznego dla domeny. Wybierając szablon, który najlepiej przypomina język, który chcesz utworzyć, możesz zminimalizować modyfikacje, które należy wykonać w rozwiązaniu początkowym.

 Poniższe szablony rozwiązań są dostępne w Kreatorze projektant języka specyficznego dla domeny.

|Formularza|Funkcje|Opis|
|-|-|-|
|Diagramy klas|Przedział — kształty<br />Dziedziczenie klasy<br />-Dziedziczenie relacji<br />-Dziedziczenie kształtu<br />-Właściwości relacji|Użyj tego szablonu rozwiązania, jeśli język specyficzny dla domeny zawiera jednostki i relacje z właściwościami. Ten szablon służy do tworzenia języka specyficznego dla domeny, który jest podobny do diagramów klas UML. Główne jednostki są klasami i interfejsami, a także z relacjami skojarzenia, generalizacji i implementacji. Klasa lub interfejs pojawia się jako pole zawierające listę atrybutów.|
|Diagramy składników|-Porty|Użyj tego szablonu rozwiązania, jeśli język specyficzny dla domeny zawiera składniki, czyli części systemu oprogramowania. Ten szablon służy do tworzenia języka specyficznego dla domeny, który jest podobny do diagramów składników UML. Główne jednostki są składnikami i portami, które są wyświetlane jako małe kształty poza składnikami.|
|Diagramy przepływu zadań|— Kształty obrazów i geometrii<br />-   *tory*|Użyj tego szablonu rozwiązania, jeśli język specyficzny dla domeny zawiera przepływy pracy, Stany lub sekwencje. Ten szablon służy do tworzenia języka specyficznego dla domeny, który jest podobny do diagramów aktywności UML. Główną jednostką jest działanie, a główna relacja jest przejściem między działaniami. Szablon zawiera kilka innych elementów, takich jak stan początkowy, stan końcowy i pasek synchronizacji.|
|Minimalny język|-Jedna klasa i kształt<br />-Jedna relacja i łącznik|Użyj tego szablonu rozwiązania, jeśli język specyficzny dla domeny nie przypomina innych szablonów. Ten szablon służy do tworzenia języka specyficznego dla domeny, który ma dwie klasy i jedną relację, która jest reprezentowana w **przyborniku** jako **pole** i **wiersz**. Każda klasa i relacja mają przykładową Właściwość ciągu.|
|Minimalny Projektant WinForm|-Mały model.<br />— Formularz systemu Windows, który wyświetla model.|Użyj tego szablonu, jeśli chcesz skompilować aplikację, w której jest powiązany DSL z formularzem systemu Windows, a nie projektantem graficznym.<br /><br /> Formularz, który działa jako interfejs użytkownika dla języka, znajduje się w folderze Dsl\UI.<br /><br /> Przed otwarciem projektanta formularzy należy skompilować projekt.<br /><br /> Aby uzyskać więcej informacji, zobacz [Tworzenie języka specyficznego dla domeny opartego na Windows Forms](../modeling/creating-a-windows-forms-based-domain-specific-language.md).|
|Minimalny Projektant WPF|-Mały model<br />-Windows Presentation Foundation interfejs użytkownika, który wyświetla model|Użyj tego szablonu, jeśli chcesz skompilować aplikację, w której jest powiązany DSL z interfejsem użytkownika WPF, a nie projektantem graficznym.<br /><br /> Projektant dla interfejsu użytkownika znajduje się w folderze Dsl\UI.<br /><br /> Należy skompilować projekt przed otwarciem projektanta interfejsu użytkownika.<br /><br /> Aby uzyskać więcej informacji, zobacz [Tworzenie języka specyficznego dla domeny opartego na platformie WPF](../modeling/creating-a-wpf-based-domain-specific-language.md).|
|Biblioteka DSL|-Minimalna Biblioteka|Użyj tego szablonu, jeśli chcesz skompilować częściową definicję DSL, którą można zaimportować do innych definicji DSL.|

## <a name="see-also"></a>Zobacz także

- [Przegląd narzędzi języka specyficznego dla domeny](../modeling/overview-of-domain-specific-language-tools.md)
