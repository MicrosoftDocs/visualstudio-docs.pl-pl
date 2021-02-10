---
title: Tworzenie kolumn witryn, typów zawartości i list dla programu SharePoint | Microsoft Docs
titleSuffix: ''
description: Tworzenie kolumn witryn, typów zawartości i list dla programu SharePoint. Program Visual Studio udostępnia szablony elementów projektu dla tych typów elementów programu SharePoint.
ms.custom: SEO-VS-2020
ms.date: 02/02/2017
ms.topic: conceptual
f1_keywords:
- VS.SharePointTools.ListDesigner.ContentTypeSetting
- VS.SharePointTools.ContentTypeDesigner.CommonPropertiesPage
- VS.SharePointTools.ListDesigner.CreatingLists
- VS.SharePointTools.ListDesigner.ListPage
- VS.SharePointTools.ListDesigner.ViewPage
- VS.SharePointTools.ListDesigner.CommonPropertiesPage
- VS.SharePointTools.ContentTypeDesigner.ColumnsPage
dev_langs:
- VB
- CSharp
author: John-Hart
ms.author: johnhart
manager: jmartens
ms.workload:
- office
ms.openlocfilehash: dfdf94f58c0fa7ba40d7c08309f8ea57949310df
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99949028"
---
# <a name="create-site-columns-content-types-and-lists-for-sharepoint"></a>Tworzenie kolumn witryn, typów zawartości i list dla programu SharePoint
  Program Visual Studio udostępnia szablony elementów projektu dla wielu różnych podstawowych elementów programu SharePoint, w tym *listy* i *typy zawartości*, które mogą obejmować kolumny witryny (lub *pola*). Nowe projektanci typów zawartości i list tworzą te elementy łatwiej niż kiedykolwiek wcześniej.

## <a name="site-columns"></a>Kolumny witryny
 Kolumny witryny są jednym z najbardziej podstawowych elementów, które można dodać do projektu programu SharePoint. Kolumna witryny reprezentuje typ danych, taki jak numer telefonu, komentarz lub nazwa miasta kontaktu na liście kontaktów.

 Nowy szablon elementu projektu kolumny witryny sprawia, że tworzenie kolumn lokacji jest łatwiejsze niż w starszej wersji programu Visual Studio. Po utworzeniu nowej kolumny witryny można zmodyfikować kod XML w pliku *Elements.xml* kolumny witryny w celu uwzględnienia żądanych informacji, takich jak nazwa wyświetlana, jej typ danych i Grupa, w której ma zostać wyświetlona kolumna lokacja w programie SharePoint. Aby uzyskać więcej informacji na temat kolumn lokacji, zobacz [wprowadzenie do kolumn](/previous-versions/office/developer/sharepoint-2010/ms450825(v=office.14)).

## <a name="content-types-and-lists"></a>Typy zawartości i listy
 Typy zawartości i listy są między najczęściej używanymi elementami w programie SharePoint.

 Typ zawartości definiuje metadane, przepływ pracy i zachowanie dla kategorii elementów na liście programu SharePoint lub w bibliotece dokumentów. Na przykład można utworzyć typ zawartości, aby uzyskać informacje na liście kontaktów lub na liście zadań. Typ zawartości kontaktu może zawierać kolumny, takie jak imię i nazwisko, adres E-mail, numer telefonu i adres. Typ zawartości zdefiniowany na poziomie witryny jest niezależny od żadnej listy lub biblioteki dokumentów w lokacji. Możesz użyć tego samego typu zawartości z różnymi listami lub bibliotekami dokumentów w witrynie programu SharePoint. Można również użyć kilku typów zawartości na tej samej liście lub w bibliotece dokumentów.

 Lista to zbiór informacji w programie SharePoint, które można udostępniać innym osobom. Listy składają się z wierszy kolumn zawierających dane. Niektóre przykłady list obejmują: listę zadań, listę kontaktów i listę anonsów.

 Nowy typ zawartości i projektanci listy w programie [!INCLUDE[vsprvs](../sharepoint/includes/vsprvs-md.md)] ułatwiają tworzenie typów zawartości witryny i wyświetlanie ich na wiele łatwiejszych i bardziej intuicyjnych niż w starszej wersji programu Visual Studio. Interfejs użytkownika umożliwia wizualne konstruowanie typów zawartości i list w znany sposób i pozwala sortować i grupować dane na listach oraz używać nagłówków grup. Aby uzyskać więcej informacji na temat typów zawartości, zobacz [typy zawartości](/previous-versions/office/developer/sharepoint-2010/ms479905(v=office.14)). Aby uzyskać więcej informacji na temat list, zobacz [list Forms](/previous-versions/office/developer/sharepoint-2010/aa543232(v=office.14)) i [widoki list](/previous-versions/office/developer/sharepoint-2010/ff604021(v=office.14)).

## <a name="related-topics"></a>Powiązane tematy

|Tytuł|Opis|
|-----------|-----------------|
|[Przewodnik: Tworzenie kolumny witryny, typu zawartości i listy dla programu SharePoint](../sharepoint/walkthrough-create-a-site-column-content-type-and-list-for-sharepoint.md)|Pokazuje, jak utworzyć kolumny witryny, które są używane w niestandardowym typie zawartości. Typ zawartości jest następnie używany na liście niestandardowej.|

## <a name="see-also"></a>Zobacz też
- [Wprowadzenie do programowania w programie SharePoint 2010](/sharepoint/dev/)
