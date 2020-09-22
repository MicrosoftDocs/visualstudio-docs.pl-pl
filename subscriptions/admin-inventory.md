---
title: Spis środowiska przedprodukcyjnego | Visual Studio Marketplace
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 7d74e113-8fb2-490e-8502-48cce7b1327a
ms.date: 03/06/2020
ms.topic: conceptual
description: Informacje o responsibilty administratorów dotyczące przeprowadzania spisów przedprodukcyjnych
ms.openlocfilehash: 1abc3c15a7bd9e47b0f449c5a49fdbbc8e7bb590
ms.sourcegitcommit: 09d1f5cef5360cdc1cdfd4b22a1a426b38079618
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2020
ms.locfileid: "91004160"
---
# <a name="inventory-of-pre-production-environment"></a>Spis środowiska przedprodukcyjnego
Subskrypcje programu Visual Studio upraszczają zarządzanie zasobami przez zliczanie użytkowników, a nie urządzeń.

Administratorzy programu Visual Studio muszą przypisywać subskrypcje programu Visual Studio do **określonych, nazwanych użytkowników**. Konwencje nazewnictwa, takie jak Dev1, Dev2 lub użycie nazw zespołów, takich jak "FeatureTeam", są **niedozwolone**.

Oto kilka sposobów, aby uprościć tworzenie spisu środowiska przedprodukcyjnego:
- Przejrzyj przypisania użytkownika. Firma Microsoft udostępnia witrynę internetową o nazwie [Portal administracyjny programu Visual Studio](https://manage.visualstudio.com/) ułatwiającą śledzenie przypisań subskrypcji programu Visual Studio.
- Użyj Active Directory lokalnego lub opartego na chmurze, aby wyświetlić listę użytkowników. Jeśli używasz Active Directory do zarządzania dostępem użytkowników, możesz identyfikować użytkowników programistycznych i testowych według ich przynależności do katalogów.
- Korzystaj z automatycznych narzędzi do spisu systemów. Może być również konieczne użycie narzędzia do spisu oprogramowania w celu ułatwienia zarządzania zasobami oprogramowania i odróżnienia środowiska przedprodukcyjnego od produkcyjnych. Wielu klientów korzystających z programu Microsoft System Center tworzy konwencje nazewnictwa, aby ułatwić automatyzację tej części procesu spisu.
- Uzyskaj pomoc dotyczącą ręcznego uzgadniania. Zarejestruj personel, aby pomóc w uzgadnianiu użytkowników programistycznych i testowych w środowisku deweloperskim i testowym.

## <a name="resources"></a>Zasoby
- [Oficjalny dokument dotyczący licencjonowana programu Visual Studio](https://visualstudio.microsoft.com/wp-content/uploads/2019/06/Visual-Studio-Licensing-Whitepaper-May-2019.pdf)
- [Pomoc techniczna dotycząca subskrypcji programu Visual Studio i administrowania nim](https://visualstudio.microsoft.com/support/support-overview-vs)
- [Postanowienia dotyczące licencjonowania zbiorowego](https://www.microsoft.com/licensing/product-licensing/products.aspx)

## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](/visualstudio/)
- [Dokumentacja usługi Azure DevOps](/azure/devops/)
- [Dokumentacja platformy Azure](/azure/)
- [Dokumentacja Microsoft 365](/microsoft-365/)

## <a name="next-steps"></a>Następne kroki
Dowiedz się więcej o odpowiedzialności dla administratorów:
- [Obowiązki administratora](admin-responsibilities.md)
- [Zarządzanie dużymi zespołami i zleceniobiorcami zewnętrznymi](manage-teams.md)
- [Śledzenie przypisań użytkowników i przetwarzanie zamówień](assignments-orders.md)
- Używanie [maksymalnego użycia](maximum-usage.md) do śledzenia zobowiązań zakupu