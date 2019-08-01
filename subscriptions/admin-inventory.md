---
title: Spis środowiska przedprodukcyjnego | Visual Studio Marketplace
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/23/2019
ms.topic: conceptual
description: Informacje o responsibilty administratorów dotyczące przeprowadzania spisów przedprodukcyjnych
ms.openlocfilehash: d400e216d81601583dc08f66f1a6a185cbe41b91
ms.sourcegitcommit: 59e5758036223ee866f3de5e3c0ab2b6dbae97b6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68423095"
---
# <a name="inventory-of-pre-production-environment"></a>Spis środowiska przedprodukcyjnego
Subskrypcje programu Visual Studio upraszczają zarządzanie zasobami przez zliczanie użytkowników, a nie urządzeń.

Administratorzy programu Visual Studio muszą przypisywać subskrypcje programu Visual Studio do **określonych, nazwanych użytkowników**. Konwencje nazewnictwa, takie jak Dev1, Dev2 lub użycie nazw zespołów, takich jak "FeatureTeam" , są niedozwolone.

Oto kilka sposobów, aby uprościć tworzenie spisu środowiska przedprodukcyjnego:
- Przejrzyj przypisania użytkownika. Firma Microsoft udostępnia witrynę internetową o nazwie [Portal administracyjny programu Visual Studio](https://manage.visualstudio.com/) ułatwiającą śledzenie przypisań subskrypcji programu Visual Studio.
- Użyj Active Directory lokalnego lub opartego na chmurze, aby wyświetlić listę użytkowników. Jeśli używasz Active Directory do zarządzania dostępem użytkowników, możesz identyfikować użytkowników programistycznych i testowych według ich przynależności do katalogów.
- Korzystaj z automatycznych narzędzi do spisu systemów. Może być również konieczne użycie narzędzia do spisu oprogramowania w celu ułatwienia zarządzania zasobami oprogramowania i odróżnienia środowiska przedprodukcyjnego od produkcyjnych. Wielu klientów korzystających z programu Microsoft System Center tworzy konwencje nazewnictwa, aby ułatwić automatyzację tej części procesu spisu.
- Uzyskaj pomoc dotyczącą ręcznego uzgadniania. Zarejestruj personel, aby pomóc w uzgadnianiu użytkowników programistycznych i testowych w środowisku deweloperskim i testowym.

## <a name="resources"></a>Zasoby
- [Oficjalny dokument dotyczący licencjonowania programu Visual Studio](https://aka.ms/vslicensing)
- [Pomoc techniczna dotycząca subskrypcji programu Visual Studio i administrowania nim](https://visualstudio.microsoft.com/support/support-overview-vs)
- [Postanowienia dotyczące licencjonowania zbiorowego](https://www.microsoft.com/licensing/product-licensing/products.aspx)

## <a name="next-steps"></a>Następne kroki
Dowiedz się więcej o odpowiedzialności dla administratorów:
- [Obowiązki administratora](admin-responsibilities.md)
- [Zarządzaj dużymi zespołami i zewnętrznymi wykonawcami](manage-teams.md)
- [Śledzenie przypisań użytkowników i zamówień procesów](assignments-orders.md)
- Używanie [maksymalnego użycia](maximum-usage.md) do śledzenia zobowiązań zakupu