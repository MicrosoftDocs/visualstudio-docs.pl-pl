---
title: Wybieranie szablonu rozwiązania dotyczącego języka specyficznego dla domeny | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- Domain-Specific Language Tools, solution templates
ms.assetid: 9c05955f-1548-4df6-b09b-4b348823c237
caps.latest.revision: 26
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 36b821219b02fa77171d89214d8cf4813ce92303
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63433391"
---
# <a name="choosing-a-domain-specific-language-solution-template"></a>Wybieranie szablonu rozwiązania dotyczącego języka specyficznego dla domeny
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Aby utworzyć rozwiązanie języka dotyczącego określonej domeny, wybierz jedną z szablonów rozwiązań, które są dostępne w Kreatorze projektanta języka specyficznego dla domeny. Wybierając szablon, który najbardziej przypomina język, który ma zostać utworzona, można zminimalizować modyfikacjach, które należy podjąć, począwszy od rozwiązania.  
  
 Następujące szablony rozwiązań są dostępne w Kreatorze projektanta języka specyficznego dla domeny.  
  
> [!NOTE]
> Celem szablonów jest zapewnienie początkowy DSL. Szablony o nazwie diagramów klas i składników nie są pełne diagramów UML. Jeśli chcesz utworzyć UML model, należy wziąć pod uwagę modelowania narzędzia, które zapewniają zestaw diagramy, które są zintegrowane w jednym modelu UML. Są rozszerzalne i może zostać zintegrowany z DSL za pomocą ModelBus. Aby uzyskać więcej informacji, zobacz [tworzenie modeli aplikacji](../modeling/create-models-for-your-app.md).  
  
|Szablon|Funkcje|Opis|  
|--------------|--------------|-----------------|  
|Diagramy klas|-Kształtów przedziałów<br />— Dziedziczenie klasa<br />-Relacji dziedziczenia<br />-Kształt dziedziczenia<br />— Właściwości relacji|Użyj tego szablonu rozwiązania, jeśli zawiera języka specyficznego dla domeny, jednostki i relacje, które mają właściwości. Ten szablon umożliwia utworzenie języka specyficznego dla domeny, podobny diagramów klas UML. Obiekty główne są klasy i interfejsy, wraz z relacji skojarzenia, generalizacji i wdrażanie. Klasy lub interfejsu jest wyświetlany jako okno, który zawiera listę atrybutów.|  
|Diagramy składników|— Porty|Użyj tego szablonu rozwiązania, jeśli języka specyficznego dla domeny obejmuje składniki, czyli części systemu oprogramowania. Ten szablon umożliwia utworzenie języka specyficznego dla domeny, który przypomina diagramy składników UML. Obiekty główne są składniki i portów, które są wyświetlane jako małe kształty na zewnątrz składników.|  
|Diagramy przepływu zadań|— Obrazów i kształtów geometrycznych<br />-   *Swimlanes*|Użyj tego szablonu rozwiązania, jeśli języka specyficznego dla domeny zawiera przepływy pracy, Państwa lub sekwencji. Ten szablon umożliwia utworzenie języka specyficznego dla domeny, który przypomina diagramy aktywności UML. Jednostki głównej jest działaniem, a relacji głównego jest przejście między działaniami. Szablon zawiera kilka innych elementów, takich jak stan początkowy stan końcowy i pasek synchronizacji.|  
|Minimalny języka|-Jedną klasę i kształt<br />-Jednej relacji i łącznik|Użyj tego szablonu rozwiązania, jeśli języka specyficznego dla domeny wygląda inaczej niż inne szablony. Ten szablon umożliwia utworzenie języka specyficznego dla domeny, który ma dwie klasy i jedna relacja, które są reprezentowane w **przybornika** jako **pole** i **wiersza**. Klasa, jak i relacji ma przykład właściwość ciągu.|  
|Minimalny projektanta formularza systemu Windows|-Małe model.<br />-Windows formularz, który wyświetla model.|Użyj tego szablonu, aby skompilować aplikację, w którym DSL jest powiązany z formularzem Windows, a nie graficznego projektanta.<br /><br /> Formularz, który działa jako interfejs użytkownika dla języka znajduje się w folderze Dsl\UI.<br /><br /> Należy skompilować projekt przed otwarciem projektanta formularzy.<br /><br /> Aby uzyskać więcej informacji, zobacz [Tworzenie języka specyficznego dla domeny Windows Forms-Based](../modeling/creating-a-windows-forms-based-domain-specific-language.md).|  
|Projektant WPF minimalny|-Małe modelu<br />— Windows Presentation Foundation interfejs użytkownika, który wyświetla model|Użyj tego szablonu, aby skompilować aplikację, w którym DSL jest powiązany z interfejsem użytkownika WPF, a nie graficznego projektanta.<br /><br /> Projektant interfejsu użytkownika znajduje się w folderze Dsl\UI.<br /><br /> Należy skompilować projekt przed otwarciem projektanta interfejsu użytkownika.<br /><br /> Aby uzyskać więcej informacji, zobacz [Tworzenie języka specyficznego dla domeny WPF-Based](../modeling/creating-a-wpf-based-domain-specific-language.md).|  
|Biblioteka DSL|— Biblioteka minimalny|Użyj tego szablonu, jeśli chcesz skompilować częściową definicję DSL, który można zaimportować do innych definicji DSL.|  
  
## <a name="see-also"></a>Zobacz też  
 [Przegląd narzędzi języka specyficznego dla domeny](../modeling/overview-of-domain-specific-language-tools.md)
