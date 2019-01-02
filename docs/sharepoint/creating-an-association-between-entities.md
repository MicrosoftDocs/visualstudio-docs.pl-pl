---
title: Tworzenie skojarzenia między jednostkami | Dokumentacja firmy Microsoft
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
author: TerryGLee
ms.author: tglee
manager: douge
ms.workload:
- office
ms.openlocfilehash: 134b477cdc199d85c983633a2a5996d113420443
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53842982"
---
# <a name="create-an-association-between-entities"></a>Tworzenie skojarzenia między jednostkami
  Możesz zdefiniować relacje między jednostkami w modelu łączności danych biznesowych (BDC) przez utworzenie skojarzenia. Program Visual Studio generuje metody udostępniające odbiorcy modelu informacje na temat każdego skojarzenia. Te metody mogą być używane przez składniki web Part programu SharePoint, list lub niestandardowych aplikacji do wyświetlania relacji między danymi w interfejsie użytkownika (UI).  
  
## <a name="create-an-association"></a>Utwórz skojarzenie
 Tworzenie skojarzenia, wybierając **skojarzenia** sterowania w programie Visual Studio **przybornika**, wybierając pierwszej jednostki (nazywane jednostki źródłowej), a następnie wybierając drugiej jednostki (o nazwie jednostki docelowej). Można zdefiniować szczegóły skojarzenia w **Edytor skojarzeń**. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie skojarzenia między jednostkami](../sharepoint/how-to-create-an-association-between-entities.md).  
  
## <a name="association-methods"></a>Metody skojarzenia
 Aplikacje, takie jak składniki web Part danych biznesowych programu SharePoint wykorzystywać skojarzenia przez wywołanie metody w klasie usługi jednostki. Możesz dodać metody do klasy usługi jednostki, wybierając je w **Edytor skojarzeń**.  
  
 Domyślnie **Edytor skojarzeń** dodaje metodę nawigacji do skojarzenia z jednostkami źródłowym i docelowym. Metoda nawigacji skojarzenia w jednostce źródłowej umożliwia konsumentów można pobrać listy jednostki docelowej. Metoda nawigacji skojarzenia w obiekcie docelowym umożliwia konsumentów pobrać jednostki źródłowej, które odnoszą się do jednostki docelowej.  
  
 Kod należy dodać do każdej z tych metod, aby zostały zwrócone odpowiednie informacje. Możesz również dodać inne rodzaje metod do obsługi bardziej zaawansowanych scenariuszy. Aby uzyskać więcej informacji na temat każdej z tych metod, zobacz [obsługiwane operacje](http://go.microsoft.com/fwlink/?LinkId=169286).  
  
## <a name="types-of-associations"></a>Typy skojarzeń
 Można tworzyć dwa typy skojarzeń w Projektancie usługi łączności danych biznesowych: obcego skojarzenia opartego na kluczach i skojarzenia bez kluczy obcych.  
  
### <a name="foreign-key-based-association"></a>Skojarzenie na podstawie klucza obcego
 Można utworzyć skojarzenia na podstawie klucza obcego, dotyczące identyfikatora w jednostce źródłowej na typ zdefiniowany w obiekcie docelowym deskryptorów. Ta relacja umożliwia modelu zapewniają rozszerzony interfejs użytkownika dla swoich użytkowników. Na przykład formularz w programie Outlook, który umożliwia użytkownikowi utworzenie zamówienia sprzedaży, który może wyświetlać klientów na liście rozwijanej; lub Podaj listę zamówień sprzedaży w programie SharePoint, która umożliwia użytkownikom otworzyć stronę profilu klienta.  
  
 Aby utworzyć skojarzenie na podstawie klucza obcego, odnoszą się identyfikatory i deskryptory, które mają taką samą nazwę i typ typu. Na przykład można utworzyć obcego skojarzenia opartego na kluczach między `Contact` jednostki i `SalesOrder` jednostki. `SalesOrder` Zwraca jednostki `ContactID` deskryptor typu jako część parametru zwracanego metody wyszukiwania lub określonej metody wyszukiwania. Zarówno deskryptory typu są wyświetlane w **Edytor skojarzeń**. Aby utworzyć obcy opartego na kluczach relację między `Contact` jednostki i `SalesOrder` jednostki, wybierz `ContactID` identyfikator obok każdego z tych pól.  
  
 Dodaj kod do metody skojarzenia Nawigator jednostki źródłowej, które zwraca kolekcję jednostki docelowej. Poniższy przykład zwraca zamówień sprzedaży dla każdego kontaktu.  
  
 [!code-csharp[SP_BDC#7](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#7)]
 [!code-vb[SP_BDC#7](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#7)]  
  
 Dodaj kod do metody skojarzenia Nawigator jednostki docelowej, która zwraca jednostki źródłowej. Poniższy przykład zwraca kontaktu, z którym powiązany jest zamówienia sprzedaży.  
  
 [!code-csharp[SP_BDC#8](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderservice.cs#8)]
 [!code-vb[SP_BDC#8](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderservice.vb#8)]  
  
### <a name="foreign-keyless-association"></a>Skojarzenie bez kluczy obcych
 Skojarzenie można utworzyć, bez mapowania identyfikatorów deskryptory typu pola. Tego rodzaju skojarzenie należy utworzyć, gdy jednostki źródłowej nie ma bezpośrednią relację z jednostki docelowej. Na przykład `SalesOrderDetail` tabela nie ma klucza obcego, która mapuje do klucza podstawowego w `Contact` tabeli.  
  
 Jeśli chcesz wyświetlić informacje w `SalesOrderDetail` tabelę, która odnosi się do `Contact`, można utworzyć skojarzenia bez kluczy obcego między `Contact` jednostki i `SalesOrderDetail` jednostki.  
  
 W ramach metody nawigacji skojarzenia `Contact` jednostki zwracanego `SalesOrderDetail` jednostek, dołączając do tabel lub przez wywołanie procedury składowanej.  
  
 Poniższy przykład zwraca szczegółowe informacje o wszystkich zamówień sprzedaży, dołączając do tabel.  
  
 [!code-csharp[SP_BDC#9](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/contactservice.cs#9)]
 [!code-vb[SP_BDC#9](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/contactservice.vb#9)]  
  
 W ramach metody nawigacji skojarzenia `SalesOrderDetail` jednostki, zwracają powiązane `Contact`. Poniższy przykład przedstawia to.  
  
 [!code-csharp[SP_BDC#10](../sharepoint/codesnippet/CSharp/SP_BDC/bdcmodel1/salesorderdetailservice.cs#10)]
 [!code-vb[SP_BDC#10](../sharepoint/codesnippet/VisualBasic/sp_bdc/bdcmodel1/salesorderdetailservice.vb#10)]  
  
## <a name="see-also"></a>Zobacz także
 [Projektowanie modelu łączności danych biznesowych](../sharepoint/designing-a-business-data-connectivity-model.md)   
 [Instrukcje: Tworzenie skojarzenia między jednostkami](../sharepoint/how-to-create-an-association-between-entities.md)  
