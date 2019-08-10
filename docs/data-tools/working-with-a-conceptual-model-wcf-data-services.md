---
title: Praca z modelem koncepcyjnym (Usługi danych programu WCF)
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- data [Visual Studio], querying a service
- data [Visual Studio], LINQ to Entities
- data [Visual Studio], querying an EDM
ms.assetid: 2cd873cf-b010-49f2-a278-bb1277aaa934
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- data-storage
ms.openlocfilehash: 677e423e456c448204d39a286509fa93aa5c57b8
ms.sourcegitcommit: 5216c15e9f24d1d5db9ebe204ee0e7ad08705347
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/09/2019
ms.locfileid: "68925339"
---
# <a name="work-with-a-conceptual-model-wcf-data-services"></a>Korzystanie z modelu koncepcyjnego (Usługi danych programu WCF)

W przypadku używania modelu koncepcyjnego do opisywania danych w bazie danych, można wysyłać zapytania o dane za pomocą obiektów, a nie do ich przetłumaczenia między schematem bazy danych i modelem obiektów.

Modeli koncepcyjnych można używać w aplikacjach Usługi danych programu WCF. W poniższych tematach przedstawiono sposób wykonywania zapytań dotyczących danych za pomocą modelu koncepcyjnego.

| Temat | Opis |
| - | - |
| [Instrukcje: Wykonaj zapytania dotyczące usługi danych](/dotnet/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services) | Pokazuje, w jaki sposób wysyłać zapytania do usługi danych z aplikacji .NET. |
| [Instrukcje: Wyniki zapytania projektu](/dotnet/framework/data/wcf/how-to-project-query-results-wcf-data-services) | Pokazuje, jak zmniejszyć ilość danych zwracanych przez zapytanie usługi danych. |

Korzystając z modelu koncepcyjnego, można określić, jakiego rodzaju dane są prawidłowe w języku zgodnym z Twoją domeną. Można zdefiniować prawidłowe dane w modelu lub można dodać sprawdzanie poprawności operacji wykonywanych w ramach jednostki lub usługi danych.

W poniższych tematach pokazano, jak dodać sprawdzanie poprawności do aplikacji Usługi danych programu WCF.

|Temat|Opis|
|-----------|-----------------|
|[Instrukcje: Komunikaty usługi przechwytywania danych](/dotnet/framework/data/wcf/how-to-intercept-data-service-messages-wcf-data-services)|Pokazuje, jak dodać weryfikację do operacji usługi danych.|

 W poniższych tematach przedstawiono sposób tworzenia, aktualizowania i usuwania danych przez wykonywanie operacji na jednostkach.

|Temat|Opis|
|-----------|-----------------|
|[Instrukcje: Dodawanie, modyfikowanie i usuwanie jednostek](/dotnet/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services)|Pokazuje, jak tworzyć, aktualizować i usuwać dane jednostki w usłudze danych.|
|[Instrukcje: Definiowanie relacji między jednostkami](/dotnet/framework/data/wcf/how-to-define-entity-relationships-wcf-data-services)|Pokazuje, jak utworzyć lub zmienić relacje w usłudze danych.|

## <a name="see-also"></a>Zobacz także

- [Usługi Windows Communication Foundation i usługi danych WCF w programie Visual Studio](../data-tools/windows-communication-foundation-services-and-wcf-data-services-in-visual-studio.md)
- [Wykonywanie zapytań do usługi danych](/dotnet/framework/data/wcf/querying-the-data-service-wcf-data-services)