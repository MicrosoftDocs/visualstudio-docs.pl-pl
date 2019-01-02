---
title: Omówienie narzędzia projektowania modelu usługi łączności danych biznesowych | Dokumentacja firmy Microsoft
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.Method_Details
- VS.SharePointTools.BDC.Explorer
- VS.SharePointTools.BDC.Diagram
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], visual tools
- Business Data Connectivity service [SharePoint development in Visual Studio], visual tools
- Business Data Connectivity service [SharePoint development in Visual Studio], BDC Explorer
- BDC [SharePoint development in Visual Studio], method details
- Business Data Connectivity service [SharePoint development in Visual Studio], designer
- Business Data Connectivity service [SharePoint development in Visual Studio], method details
- BDC [SharePoint development in Visual Studio], BDC Explorer
- BDC [SharePoint development in Visual Studio], designer
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: e4b2a094d33088adb9aa3fc2c0fba953030c781b
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53923338"
---
# <a name="bdc-model-design-tools-overview"></a>Omówienie narzędzi projektowania modelu BDC
  Można zaprojektować modelu łączności danych biznesowych (BDC) przy użyciu projektanta łączności danych biznesowych **szczegóły metody BDC** oknie i **Eksplorator BDC**.  
  
 **Eksplorator BDC** pozwala na przeglądanie modelu, model wyszukiwania i zdefiniuj deskryptory typu.  
  
## <a name="bdc-designer"></a>Projektant BDC
 W Projektancie usługi łączności danych biznesowych umożliwia do definiowania jednostek w modelu oraz wizualnie rozmieszczanie ich wzajemne relacje ze sobą. Za pomocą projektanta łączności danych biznesowych do wykonywania następujących zadań:  
  
- Dodawanie jednostki do modelu.  
  
- Usuń jednostki z modelu.  
  
- Definiowanie relacji między jednostkami.  
  
  Aby otworzyć projektanta usługi łączności danych biznesowych, kliknij dwukrotnie plik modelu w swoim projekcie lub Otwórz menu skrótów dla pliku modelu, a następnie wybierz **Otwórz**. Dodawanie jednostki do modelu przez przeciąganie lub kopiowanie **jednostki** z **przybornika** do projektanta. Aby utworzyć skojarzenie między dwiema jednostkami, wybierz opcję **skojarzenia** w kontrolce **przybornika**, wybierz pierwszy obiekt, a następnie wybierz drugiej jednostki.  
  
## <a name="bdc-method-details-window"></a>Okno Szczegóły metody BDC
 Użyj **szczegóły metody BDC** okno, aby zdefiniować parametry, wystąpień i deskryptory metody filtrów.  
  
 Można szybko wygenerować metody wyszukiwania, określonej metody wyszukiwania, twórcy, aktualizacji i Deleter w **szczegóły metody BDC** okna. Podczas generowania tych metod, program Visual Studio dodaje metadane, takie jak parametry, wystąpienia i deskryptory typu, do metody. Możesz zmodyfikować te metadane do spełnienia określonego scenariusza.  
  
 Aby otworzyć **szczegóły metody BDC** okna, na pasku menu wybierz **widoku** > **Windows inne** > **szczegóły metody BDC** .  
  
 Aby wyświetlić metod w **szczegóły metody BDC** oknie Wybierz jednostkę w Projektancie usługi łączności danych biznesowych. Metody wybranej jednostki są wyświetlane w **szczegóły metody BDC** okna. Jeśli nie wybierzesz jednostkę w Projektancie usługi łączności danych biznesowych **szczegóły metody BDC** oknie zostaną wyświetlone żadne informacje.  
  
 Rozwiń lub Zwiń węzłów w **szczegóły metody BDC** okno, aby zdefiniować parametry, wystąpień i deskryptory filtrów. Użyj **Eksplorator BDC** do definiowania deskryptory typu.  
  
## <a name="bdc-explorer"></a>Eksplorator modelu BDC
 **Eksplorator BDC** Wyświetla elementy, które tworzą model. Aby otworzyć **Eksplorator BDC**, na pasku menu wybierz **widoku** > **Windows inne** > **Eksplorator BDC**. Aby przeglądać model, rozwiń węzły w **Eksplorator BDC**. Każdy węzeł reprezentuje element w pliku XML w pliku modelu.  
  
 Podczas wybierania węzły w **Eksplorator BDC**, właściwości każdego węzła, który wybierzesz są wyświetlane w **właściwości** okna. Wiele z tych właściwości odnoszą się do atrybutów w pliku modelu. Możesz wyszukiwać modelu przy użyciu pola wyszukiwania w górnej części **Eksplorator BDC**.  
  
> [!NOTE]  
>  **Eksplorator BDC** nie wyświetla identyfikatorów, właściwości niestandardowe, zlokalizowanych ciągów, grup skojarzeń, akcje, deskryptory filtrów, list kontroli akcji i wartości domyślne parametrów.  
  
### <a name="define-type-descriptors"></a>Zdefiniuj deskryptory typu
 Użyj **Eksplorator BDC** do definiowania deskryptory typu. Eksplorator BDC pozwala zdefiniować deskryptor typu jeden raz i ponownie użyć tego deskryptora typu, gdzie indziej w modelu. Aby to osiągnąć, skopiuj deskryptor typu i wkleić go do innych parametrów lub deskryptor typu.  
  
> [!NOTE]  
>  Oryginalny deskryptor typu zmiany nie wpływają na kopie ten deskryptor typu.  
  
 Aby uzyskać więcej informacji, zobacz [jak: Określanie deskryptora typu parametru](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).  
  
## <a name="see-also"></a>Zobacz także
 [Instrukcje: Tworzenie modelu BDC](../sharepoint/how-to-create-a-bdc-model.md)   
 [Instrukcje: Dodawanie jednostki do modelu](../sharepoint/how-to-add-an-entity-to-a-model.md)   
 [Instrukcje: Dodawanie metody wyszukiwania](../sharepoint/how-to-add-a-finder-method.md)   
 [Instrukcje: Dodawanie określonej metody wyszukiwania](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Instrukcje: Dodawanie metody Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Instrukcje: Dodawanie metody Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Instrukcje: Dodawanie metody Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Tworzenie skojarzenia między jednostkami](../sharepoint/creating-an-association-between-entities.md)   
 [Przewodnik: Tworzenie listy zewnętrznej w SharePoint za pomocą danych biznesowych](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)   
 [Integrowanie danych biznesowych programu SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)   
 [Tworzenie modelu łączności danych biznesowych](../sharepoint/creating-a-business-data-connectivity-model.md)   
 [Projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md)  
