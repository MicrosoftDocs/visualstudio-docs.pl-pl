---
title: 'Instrukcje: Tworzenie skojarzenia między jednostkami | Dokumentacja firmy Microsoft'
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: eaaa3f86cc0751b0b80d61555a69aa6bfecda2f0
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53878250"
---
# <a name="how-to-create-an-association-between-entities"></a>Instrukcje: Tworzenie skojarzenia między jednostkami
  Możesz zdefiniować relacje między jednostkami w modelu łączności danych biznesowych (BDC) przez utworzenie skojarzenia. Program Visual Studio generuje metody udostępniające odbiorcy modelu informacje na temat każdego skojarzenia. Te metody mogą być używane przez składniki web Part programu SharePoint, list lub niestandardowych aplikacji do wyświetlania relacji między danymi w interfejsie użytkownika (UI).  
  
 Można tworzyć dwa typy skojarzeń w Projektancie usługi łączności danych biznesowych: obcego skojarzenia opartego na kluczach i skojarzenia bez kluczy obcych. Aby uzyskać więcej informacji, zobacz [Tworzenie skojarzenia między jednostkami](../sharepoint/creating-an-association-between-entities.md).  
  
### <a name="to-create-an-association-between-entities"></a>Aby utworzyć skojarzenia między jednostkami  
  
1.  Na **BusinessDataConnectivity** karcie **przybornika**, wybierz **skojarzenia** elementu.  
  
2.  W Projektancie usługi łączności danych biznesowych wybierz jednostki źródłowej, a następnie wybierz jednostki docelowej.  
  
     **Edytor skojarzeń** pojawia się.  
  
3.  Aby utworzyć skojarzenie opartego na kluczach obcych, należy zaznaczyć **jest skojarzeniem klucza obcego** pole wyboru.  
  
    1.  W **identyfikator źródłowego** kolumny **mapowanie identyfikatora** tabeli, wybierz identyfikator obok każdego pasującego deskryptora typu, który pojawia się w **pola** kolumny.  
  
         Na przykład w **identyfikator źródłowego** kolumny wybierz `ContactID` obok `ReadList.salesOrderList.SalesOrderList.SalesOrder.ContactID` deskryptor typu i `ReadItem.salesOrder.SalesOrder.ContactID` deskryptor typu.  
  
4.  Jeśli chcesz utworzyć skojarzenie bez kluczy obcych, wyczyść **jest skojarzeniem klucza obcego** pole wyboru.  
  
5.  Wybierz **OK** przycisku.  
  
6.  W Projektancie usługi łączności danych biznesowych wiersza, który reprezentuje skojarzenia pojawia się między jednostki źródłowej i jednostki docelowej.  
  
     Visual Studio dodaje metodę Nawigator skojarzenia klasy usługi obiektu docelowego i Klasa usług jednostki źródłowej. Aby uzyskać więcej informacji na temat metod nawigacji skojarzenia zobacz [obsługiwane operacje](http://go.microsoft.com/fwlink/?LinkId=169286).  
  
7.  W metodzie Nawigator skojarzenia jednostki źródłowej Dodaj kod, który zwraca kolekcję jednostki docelowej.  
  
8.  W metodzie Nawigator skojarzenie obiektu docelowego Dodaj kod, który zwraca jednostki źródłowej powiązane.  
  
     Przykłady Nawigator skojarzenia metody, zobacz [Tworzenie skojarzenia między jednostkami](../sharepoint/creating-an-association-between-entities.md).  
  
## <a name="see-also"></a>Zobacz także
 [Tworzenie skojarzenia między jednostkami](../sharepoint/creating-an-association-between-entities.md)   
 [Projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Instrukcje: Dodawanie metody wyszukiwania](../sharepoint/how-to-add-a-finder-method.md)   
 [Instrukcje: Dodawanie określonej metody wyszukiwania](../sharepoint/how-to-add-a-specific-finder-method.md)   
 [Instrukcje: Dodawanie metody Creator](../sharepoint/how-to-add-a-creator-method.md)   
 [Instrukcje: Dodawanie metody Deleter](../sharepoint/how-to-add-a-deleter-method.md)   
 [Instrukcje: Dodawanie metody Updater](../sharepoint/how-to-add-an-updater-method.md)   
 [Omówienie narzędzi projektowania modelu BDC](../sharepoint/bdc-model-design-tools-overview.md)   
 [Instrukcje: Dodaj parametr do metody](../sharepoint/how-to-add-a-parameter-to-a-method.md)   
 [Instrukcje: Definiowanie wystąpienia metody](../sharepoint/how-to-define-a-method-instance.md)   
 [Instrukcje: Określanie deskryptora typu parametru](../sharepoint/how-to-define-the-type-descriptor-of-a-parameter.md)   
 [Przewodnik: Tworzenie listy zewnętrznej w SharePoint za pomocą danych biznesowych](../sharepoint/walkthrough-creating-an-external-list-in-sharepoint-by-using-business-data.md)  
