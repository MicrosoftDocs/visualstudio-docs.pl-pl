---
title: Omówienie narzędzi projektowania modelu BDC | Microsoft Docs
description: Zapoznaj się z omówieniem narzędzi do projektowania, które mają być używane z modelem łączności danych biznesowych (BDC). Dowiedz się więcej na temat projektanta BDC, okna Szczegóły metody BDC i Eksploratora usługi BDC.
ms.custom: SEO-VS-2020
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
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: b398d9c00caf3a4fa2ca58bafa3273673a305859
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99851689"
---
# <a name="bdc-model-design-tools-overview"></a>Omówienie narzędzi projektowania modelu BDC
  Model łączności danych biznesowych (BDC) można zaprojektować za pomocą projektanta BDC, okna **Szczegóły metody BDC** i **Eksploratora usługi BDC**.

 **Eksplorator usługi BDC** pozwala przeglądać model, przeszukiwać model i definiować deskryptory typów.

## <a name="bdc-designer"></a>Projektant BDC
 Projektant BDC umożliwia zdefiniowanie jednostek w modelu i wizualne rozmieszczenie relacji ze sobą. Za pomocą projektanta usługi BDC można wykonywać następujące zadania:

- Dodaj jednostki do modelu.

- Usuń jednostki z modelu.

- Zdefiniuj relacje między jednostkami.

  Aby otworzyć projektanta usługi BDC, kliknij dwukrotnie plik modelu w projekcie lub Otwórz menu skrótów dla pliku modelu, a następnie wybierz polecenie **Otwórz**. Dodaj jednostkę do modelu, przeciągając lub kopiując **jednostkę** z **przybornika** do projektanta. Aby utworzyć skojarzenie między dwiema jednostkami, wybierz kontrolkę **skojarzenie** w **przyborniku**, wybierz pierwszą jednostkę, a następnie wybierz drugą jednostkę.

## <a name="bdc-method-details-window"></a>Okno Szczegóły metody BDC
 Okno **Szczegóły metody BDC** służy do definiowania parametrów, wystąpień i deskryptorów filtrów metody.

 W oknie **Szczegóły metody BDC** można szybko wygenerować wyszukiwanie, określone metody wyszukiwania, twórców, Aktualizator i metod Delete. Podczas generowania tych metod program Visual Studio dodaje do metody metadane, takie jak parametry, wystąpienia i deskryptory typu. Możesz zmodyfikować te metadane, aby spełniały określony scenariusz.

 Aby otworzyć okno **Szczegóły metody BDC** , na pasku menu wybierz opcję **Wyświetl**  >  **inne**  >  **Szczegóły metody BDC** systemu Windows.

 Aby wyświetlić metody w oknie **Szczegóły metody BDC** , wybierz jednostkę w projektancie BDC. Metody wybranej jednostki pojawiają się w oknie **Szczegóły metody BDC** . Jeśli nie wybierzesz jednostki w Projektancie usługi BDC, w oknie **Szczegóły metody BDC** nie zostaną wyświetlone żadne informacje.

 Rozwiń lub Zwiń węzły w oknie **Szczegóły metody BDC** , aby zdefiniować parametry, wystąpienia i deskryptory filtrów. Zdefiniuj deskryptory typu za pomocą **Eksploratora łączności danych biznesowych** .

## <a name="bdc-explorer"></a>Eksplorator modelu BDC
 W **Eksploratorze BDC** są wyświetlane elementy wchodzące w skład modelu. Aby otworzyć **Eksploratora usługi BDC**, na pasku menu wybierz pozycję **Wyświetl**  >  **inne**  >  **Eksplorator usługi Windows BDC**. Aby przeglądać model, rozwiń węzły w **Eksploratorze BDC**. Każdy węzeł reprezentuje element w kodzie XML pliku modelu.

 Po wybraniu węzłów w **Eksploratorze BDC** właściwości każdego wybranego węzła są wyświetlane w oknie **Właściwości** . Wiele z tych właściwości odpowiada atrybutom w pliku modelu. Możesz przeszukiwać model przy użyciu pola wyszukiwania w górnej części okna **Eksplorator usługi BDC**.

> [!NOTE]
> **Eksplorator usługi BDC** nie wyświetla identyfikatorów, właściwości niestandardowych, zlokalizowanych ciągów, grup skojarzeń, akcji, deskryptorów filtrów, list kontrolek akcji i wartości domyślnych parametrów.

### <a name="define-type-descriptors"></a>Definiowanie deskryptorów typu
 Zdefiniuj deskryptory typu za pomocą **Eksploratora łączności danych biznesowych** . Eksplorator usługi BDC umożliwia zdefiniowanie deskryptora typu jeden raz, a następnie ponowne użycie tego deskryptora typu w innym miejscu w modelu. Aby to osiągnąć, skopiuj deskryptor typu i wklej go do dowolnego innego parametru lub deskryptora typu.

> [!NOTE]
> Zmiany w oryginalnym deskryptorze typu nie mają wpływu na kopie tego deskryptora typu.

 Aby uzyskać więcej informacji, zobacz [How to: define The Type Descriptor of a Parameter](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md).

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Tworzenie modelu usługi BDC](../sharepoint/how-to-create-a-bdc-model.md)
- [Instrukcje: Dodawanie jednostki do modelu](../sharepoint/how-to-add-an-entity-to-a-model.md)
- [Instrukcje: Dodawanie metody wyszukiwania](../sharepoint/how-to-add-a-finder-method.md)
- [Instrukcje: dodawanie określonej metody wyszukiwania](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Instrukcje: Dodawanie metody Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Instrukcje: Dodawanie metody usuwania](../sharepoint/how-to-add-a-deleter-method.md)
- [Instrukcje: Dodawanie metody Aktualizator](../sharepoint/how-to-add-an-updater-method.md)
- [Utwórz skojarzenie między jednostkami](../sharepoint/creating-an-association-between-entities.md)
- [Przewodnik: Tworzenie listy zewnętrznej w programie SharePoint przy użyciu danych firmowych](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)
- [Integrowanie danych firmowych z programem SharePoint](../sharepoint/integrating-business-data-into-sharepoint.md)
- [Tworzenie modelu łączności danych firmy](../sharepoint/creating-a-business-data-connectivity-model.md)
- [Projektowanie modelu łączności danych firmy](../sharepoint/designing-a-business-data-connectivity-model.md)
