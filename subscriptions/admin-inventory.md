---
title: Wykaz środowisk przedprodukcyjnych | Visual Studio Marketplace
author: evanwindom
ms.author: lank
manager: lank
ms.assetid: 7d74e113-8fb2-490e-8502-48cce7b1327a
ms.date: 03/06/2020
ms.topic: conceptual
description: Dowiedz się więcej o odpowiedzialności administratorów za prowadzenie zapasów przedprodukcyjnych
ms.openlocfilehash: dc307d9d2f83666c6648a35b3e28a81da2de5c38
ms.sourcegitcommit: eeff6f675e7850e718911647343c5df642063d5e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80232760"
---
# <a name="inventory-of-pre-production-environment"></a>Inwentaryzacja środowiska przedprodukcyjnyego
Subskrypcje programu Visual Studio upraszczają zarządzanie zasobami, licząc użytkowników, a nie urządzenia.

Administratorzy programu Visual Studio muszą przypisywać subskrypcje programu Visual Studio **określonym osobom o nazwie**. Nie **wolno**nazywać konwencji, takich jak Dev1, Dev2 lub nazwy zespołów, takich jak "FeatureTeam".

Oto kilka sposobów na uproszczenie inwentaryzacji środowiska przedprodukcowego:
- Przejrzyj przypisania użytkowników. Firma Microsoft udostępnia witrynę sieci Web o nazwie [Portal administracyjny programu Visual Studio,](https://manage.visualstudio.com/) aby ułatwić śledzenie przydziałów subskrypcji programu Visual Studio.
- Użyj lokalnej lub chmurowej usługi Active Directory do listy użytkowników. Jeśli używasz usługi Active Directory do zarządzania dostępem użytkowników, możesz zidentyfikować użytkowników programistów i przetestować według ich członkostwa w katalogu.
- Używaj zautomatyzowanych narzędzi do magazynowania systemów. Może być również konieczne użycie narzędzia do inwentaryzacji oprogramowania, aby ułatwić zarządzanie zasobami oprogramowania i odróżnianie środowisk przedprodukcyjnych od środowisk produkcyjnych. Wielu klientów korzystających z programu Microsoft System Center tworzy konwencje nazewnictwa, aby zautomatyzować tę część procesu zapasów.
- Uzyskaj pomoc dotyczącą ręcznego uzgadniania. Zaciągnij swoich pracowników, aby pomóc w uzgodnieniu deweloperów i testowania użytkowników ze środowiskiem deweloperskim i testowym.

## <a name="resources"></a>Resources
- [Oficjalny dokument dotyczący licencjonowana programu Visual Studio](https://visualstudio.microsoft.com/wp-content/uploads/2019/06/Visual-Studio-Licensing-Whitepaper-May-2019.pdf)
- [Pomoc techniczna dotycząca subskrypcji programu Visual Studio i administrowania nim](https://visualstudio.microsoft.com/support/support-overview-vs)
- [Postanowienia licencjonowania zbiorowego](https://www.microsoft.com/licensing/product-licensing/products.aspx)

## <a name="see-also"></a>Zobacz też
- [Dokumentacja programu Visual Studio](https://docs.microsoft.com/visualstudio/)
- [Dokumentacja usługi Azure DevOps](https://docs.microsoft.com/azure/devops/)
- [Dokumentacja platformy Azure](https://docs.microsoft.com/azure/)
- [Dokumentacja usługi Microsoft 365](https://docs.microsoft.com/microsoft-365/)

## <a name="next-steps"></a>Następne kroki
Dowiedz się więcej o obowiązkach administratorów:
- [Obowiązki administratora](admin-responsibilities.md)
- [Zarządzanie dużymi zespołami i zleceniobiorcami zewnętrznymi](manage-teams.md)
- [Śledzenie przypisań użytkowników i przetwarzanie zamówień](assignments-orders.md)
- Śledzenie zobowiązań dotyczących zakupu za pomocą [maksymalnego użycia](maximum-usage.md)



