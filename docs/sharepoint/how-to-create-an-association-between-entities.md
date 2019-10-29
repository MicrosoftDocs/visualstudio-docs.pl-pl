---
title: 'Instrukcje: Tworzenie skojarzenia między jednostkami | Microsoft Docs'
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- AssociationGroupTool
dev_langs:
- VB
- CSharp
helpviewer_keywords:
- BDC [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associations between entities
- BDC [SharePoint development in Visual Studio], associations between entities
- Business Data Connectivity service [SharePoint development in Visual Studio], create an assocation
- Business Data Connectivity service [SharePoint development in Visual Studio], associate external content types
- Business Data Connectivity service [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], relate entities
- BDC [SharePoint development in Visual Studio], associate external content types
author: John-Hart
ms.author: johnhart
manager: jillfra
ms.workload:
- office
ms.openlocfilehash: cba9d712e2bcfa90ae37d47e3c518697f10b6add
ms.sourcegitcommit: dcbb876a5dd598f2538e62e1eabd4dc98595b53a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/28/2019
ms.locfileid: "72981833"
---
# <a name="how-to-create-an-association-between-entities"></a>Instrukcje: Tworzenie skojarzenia między jednostkami
  Możesz definiować relacje między jednostkami w modelu łączności danych biznesowych (BDC), tworząc skojarzenia. Program Visual Studio generuje metody zapewniające odbiorcom modelu informacje o każdym skojarzeniu. Te metody mogą być używane przez składniki Web Part programu SharePoint, listy lub aplikacje niestandardowe do wyświetlania relacji danych w interfejsie użytkownika.

 W projektancie BDC można utworzyć dwa typy skojarzeń: skojarzenia oparte na klucz obcy i obce. Aby uzyskać więcej informacji, zobacz [Tworzenie skojarzenia między jednostkami](../sharepoint/creating-an-association-between-entities.md).

### <a name="to-create-an-association-between-entities"></a>Aby utworzyć skojarzenie między jednostkami

1. Na karcie **BusinessDataConnectivity** w **przyborniku**wybierz element **skojarzenia** .

2. W projektancie BDC wybierz jednostkę źródłową, a następnie wybierz jednostkę docelową.

     Zostanie wyświetlony **Edytor skojarzeń** .

3. Jeśli chcesz utworzyć skojarzenie oparte na kluczu obcym, zaznacz pole wyboru **czy jest to skojarzenie klucza obcego** .

    1. W kolumnie **identyfikator źródła** tabeli **Mapowanie identyfikatora** wybierz identyfikator obok każdego zgodnego deskryptora typu, który pojawia się w kolumnie **pole** .

         Na przykład w kolumnie **identyfikator źródła** wybierz `ContactID` obok deskryptora typu `ReadList.salesOrderList.SalesOrderList.SalesOrder.ContactID` i deskryptora typu `ReadItem.salesOrder.SalesOrder.ContactID`.

4. Jeśli chcesz utworzyć skojarzenie z obcym kluczem, usuń zaznaczenie pola wyboru **to skojarzenie klucza obcego** .

5. Wybierz przycisk **OK** .

6. W projektancie BDC wiersz reprezentujący skojarzenie pojawia się między jednostką źródłową a jednostką docelową.

     Program Visual Studio dodaje metodę nawigatora skojarzenia do klasy usługi jednostki docelowej i klasy usługi jednostki źródłowej. Aby uzyskać więcej informacji na temat metod nawigacji skojarzenia, zobacz [obsługiwane operacje](/previous-versions/office/developer/sharepoint-2010/ee557363(v=office.14)).

7. W metodzie nawigatora skojarzenia jednostki źródłowej Dodaj kod, który zwraca kolekcję jednostek docelowych.

8. W metodzie nawigatora skojarzenia jednostki docelowej Dodaj kod, który zwraca powiązaną jednostkę źródłową.

     Przykłady metod nawigatora skojarzeń można znaleźć w temacie [Tworzenie skojarzenia między jednostkami](../sharepoint/creating-an-association-between-entities.md).

## <a name="see-also"></a>Zobacz także
- [Utwórz skojarzenie między jednostkami](../sharepoint/creating-an-association-between-entities.md)
- [Projektowanie modelu łączności danych firmy](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Instrukcje: Dodawanie metody wyszukiwania](../sharepoint/how-to-add-a-finder-method.md)
- [Instrukcje: dodawanie określonej metody wyszukiwania](../sharepoint/how-to-add-a-specific-finder-method.md)
- [Instrukcje: Dodawanie metody Creator](../sharepoint/how-to-add-a-creator-method.md)
- [Instrukcje: Dodawanie metody usuwania](../sharepoint/how-to-add-a-deleter-method.md)
- [Instrukcje: Dodawanie metody Aktualizator](../sharepoint/how-to-add-an-updater-method.md)
- [Omówienie narzędzi projektowania modelu BDC](../sharepoint/bdc-model-design-tools-overview.md)
- [Instrukcje: Dodawanie parametru do metody](../sharepoint/how-to-add-a-parameter-to-a-method.md)
- [Instrukcje: Definiowanie wystąpienia metody](../sharepoint/how-to-define-a-method-instance.md)
- [Instrukcje: Definiowanie deskryptora typu dla parametru](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)
- [Przewodnik: Tworzenie listy zewnętrznej w programie SharePoint przy użyciu danych firmowych](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)
