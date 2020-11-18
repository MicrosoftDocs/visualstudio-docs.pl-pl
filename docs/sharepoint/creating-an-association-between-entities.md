---
title: Tworzenie skojarzenia między jednostkami | Microsoft Docs
description: Utwórz skojarzenie między jednostkami w modelu łączności danych biznesowych (BDC). Dowiedz się więcej o metodach skojarzenia i typach skojarzeń.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.BDC.Association_Dialog
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
ms.openlocfilehash: 6a5decf8ad803bea8b1d64c79410c319dbef0be9
ms.sourcegitcommit: ad2c820b280b523a7f7aef89742cdb719354748f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/18/2020
ms.locfileid: "94850549"
---
# <a name="create-an-association-between-entities"></a>Utwórz skojarzenie między jednostkami
  Możesz definiować relacje między jednostkami w modelu łączności danych biznesowych (BDC), tworząc skojarzenia. Program Visual Studio generuje metody zapewniające odbiorcom modelu informacje o każdym skojarzeniu. Te metody mogą być używane przez składniki Web Part programu SharePoint, listy lub aplikacje niestandardowe do wyświetlania relacji danych w interfejsie użytkownika.

## <a name="create-an-association"></a>Tworzenie skojarzenia
 Utwórz skojarzenie, wybierając kontrolkę **skojarzenia** w **przyborniku** programu Visual Studio, wybierając pierwszą jednostkę (o nazwie jednostka źródłowa), a następnie wybierając drugą jednostkę (nazywaną jednostką docelową). Można zdefiniować szczegóły skojarzenia w **Edytorze skojarzenia**. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie skojarzenia między jednostkami](../sharepoint/how-to-create-an-association-between-entities.md).

## <a name="association-methods"></a>Metody kojarzenia
 Aplikacje, takie jak składniki Web Part programu SharePoint Business, wykorzystują skojarzenia przez wywoływanie metod w klasie usługi jednostki. Możesz dodać metody do klasy usługi jednostki, wybierając je w **Edytorze skojarzenia**.

 Domyślnie **Edytor skojarzeń** dodaje metodę nawigacji skojarzenia do jednostki źródłowej i docelowej. Metoda nawigacji skojarzenia w jednostce źródłowej umożliwia konsumentom Pobieranie listy jednostek docelowych. Metoda nawigacji skojarzenia w jednostce docelowej umożliwia konsumentom pobranie jednostki źródłowej powiązanej z jednostką docelową.

 Aby zwrócić odpowiednie informacje, należy dodać kod do każdej z tych metod. Możesz również dodać inne typy metod, aby obsługiwać bardziej zaawansowane scenariusze. Aby uzyskać więcej informacji na temat każdej z tych metod, zobacz [obsługiwane operacje](/previous-versions/office/developer/sharepoint-2010/ee557363(v=office.14)).

## <a name="types-of-associations"></a>Typy skojarzeń
 W projektancie BDC można utworzyć dwa typy skojarzeń: skojarzenia oparte na klucz obcy i obce.

### <a name="foreign-key-based-association"></a>Skojarzenie oparte na kluczu obcym
 Można utworzyć skojarzenie oparte na kluczu obcym, odnoszące się do identyfikatora w jednostce źródłowej, aby wpisać deskryptory zdefiniowane w jednostce docelowej. Ta relacja umożliwia klientom modelu zapewnienie rozszerzonego interfejsu użytkownika dla użytkowników. Na przykład formularz w programie Outlook, który umożliwia użytkownikowi tworzenie zamówienia sprzedaży, które może wyświetlać klientów na liście rozwijanej. lub Lista zamówień sprzedaży w programie SharePoint, która umożliwia użytkownikom otwieranie strony profilu dla klienta.

 Aby utworzyć skojarzenie oparte na kluczu obcym, odnoszące się do identyfikatorów i deskryptorów typu, które mają taką samą nazwę i typ. Na przykład można utworzyć skojarzenie oparte na kluczu obcym między `Contact` jednostką i `SalesOrder` jednostką. `SalesOrder`Jednostka zwraca `ContactID` deskryptor typu jako część parametru zwracanego wyszukiwania lub określonych metod wyszukiwania. Oba deskryptory typów są wyświetlane w **Edytorze skojarzeń**. Aby utworzyć relację opartą na kluczu obcym między `Contact` jednostką i `SalesOrder` jednostką, wybierz `ContactID` Identyfikator obok każdego z tych pól.

 Dodaj kod do metody nawigatora skojarzenia jednostki źródłowej, która zwraca kolekcję jednostek docelowych. Poniższy przykład zwraca zamówienia sprzedaży dla kontaktu.

 [!code-csharp[SP_BDC#7](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#7)]
 [!code-vb[SP_BDC#7](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#7)]

 Dodaj kod do metody nawigatora skojarzenia jednostki docelowej, która zwraca jednostkę źródłową. Poniższy przykład zwraca kontakt, który jest powiązany z kolejnością sprzedaży.

 [!code-csharp[SP_BDC#8](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#8)]
 [!code-vb[SP_BDC#8](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#8)]

### <a name="foreign-keyless-association"></a>Skojarzenie z niemniejszym obcym
 Można utworzyć skojarzenie bez mapowania identyfikatorów do deskryptorów typów pól. Utwórz ten rodzaj skojarzenia, gdy jednostka źródłowa nie ma bezpośredniej relacji z jednostką docelową. Na przykład tabela nie `SalesOrderDetail` ma klucza obcego, który jest mapowany na klucz podstawowy w `Contact` tabeli.

 Jeśli chcesz wyświetlić informacje w `SalesOrderDetail` tabeli, która odnosi się do `Contact` , można utworzyć obce skojarzenie między `Contact` jednostką i `SalesOrderDetail` jednostką.

 W metodzie nawigacji skojarzenia `Contact` jednostki Zwróć `SalesOrderDetail` jednostki przez przyłączenie tabel lub wywołanie procedury składowanej.

 Poniższy przykład zwraca szczegółowe informacje o wszystkich zamówieniach sprzedaży przez Sprzęganie tabel.

 [!code-csharp[SP_BDC#9](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#9)]
 [!code-vb[SP_BDC#9](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#9)]

 W metodzie nawigacji skojarzenia `SalesOrderDetail` jednostki Zwróć pokrewne `Contact` . Poniższy przykład ilustruje to.

 [!code-csharp[SP_BDC#10](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs#10)]
 [!code-vb[SP_BDC#10](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb#10)]

## <a name="see-also"></a>Zobacz także
- [Projektowanie modelu łączności danych firmy](../sharepoint/designing-a-business-data-connectivity-model.md)
- [Instrukcje: Tworzenie skojarzenia między jednostkami](../sharepoint/how-to-create-an-association-between-entities.md)
