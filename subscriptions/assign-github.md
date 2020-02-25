---
title: Oferta programu Visual Studio i usługi GitHub Enterprise | Microsoft Docs
author: evanwindom
ms.author: lank
manager: lank
ms.date: 07/28/2019
ms.topic: conceptual
description: Zarządzanie subskrypcjami w ofercie programu Visual Studio i usługi GitHub Enterprise
ms.openlocfilehash: 524002b875375c22da67bbf98d98f4ebc149c14b
ms.sourcegitcommit: bf2e9d4ff38bf5b62b8af3da1e6a183beb899809
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2020
ms.locfileid: "77558153"
---
# <a name="manage-visual-studio-subscriptions-with-github-enterprise"></a>Zarządzanie subskrypcjami programu Visual Studio za pomocą usługi GitHub Enterprise
Klienci, którzy mają umowę Enterprise Agreement (EA) z firmą Microsoft, mogą zakupić nową ofertę subskrypcji, która wiąże się z subskrypcjami programu Visual Studio w wersji Standard i usługi GitHub. Jest to prosty i ekonomiczny sposób, w jaki Subskrybenci programu Visual Studio mogą uzyskać przedsiębiorstwo w serwisie GitHub. 

Gdy organizacja kupuje subskrypcje programu Visual Studio za pomocą usługi GitHub Enterprise, są one obsługiwane i zarządzane w dwóch częściach.

## <a name="manage-visual-studio-subscriptions"></a>Zarządzanie subskrypcjami programu Visual Studio
Gdy organizacja kupuje subskrypcje programu Visual Studio za pomocą usługi GitHub Enterprise, część subskrypcji programu Visual Studio jest obsługiwana natychmiast, a subskrypcje są dostępne do przypisania i zarządzania w portalu [administracyjnym subskrypcji](https://manage.visualstudio.com) programu Visual Studio. 

Aby uzyskać więcej informacji na temat zarządzania subskrypcjami, zapoznaj się z następującymi tematami:
- [Korzystanie z portalu administracyjnego](using-admin-portal.md)
- [Przypisywanie subskrypcji](assign-license.md)
- [Edytowanie subskrypcji](edit-license.md)
- [Usuwanie subskrypcji](delete-license.md)
- [Nadmierne alokacje](handle-overclaimed-license.md)

> [!Important]
> Jeśli subskrypcje programu Visual Studio z usługą GitHub Enterprise są przypisane przez administratorów subskrypcji programu Visual Studio, a nigdy nie zakupionych subskrypcji, nie będą one widoczne dla administratorów przedsiębiorstwa usługi GitHub w organizacji. Aby upewnić się, że subskrypcje w witrynie GitHub są widoczne, należy dokonać zakupu, w tym **co najmniej jeden** Visual Studio Professional z usługą GitHub enterprise lub Visual Studio Enterprise z subskrypcją usługi GitHub Enterprise, przy pierwszym przypisaniu subskrypcji.  
>
> Klient jest odpowiedzialny za zagwarantowanie, że dla każdej przypisanej subskrypcji usługi GitHub istnieje odpowiedni program Visual Studio z subskrypcją usługi GitHub przypisany w portalu zarządzania w celu zachowania zgodności z wymaganiami dotyczącymi licencjonowania dla tego ramach.

## <a name="manage-github-enterprise-subscriptions"></a>Zarządzanie subskrypcjami w witrynie GitHub Enterprise
W przypadku zakupu subskrypcji usługi GitHub przedsiębiorstwa partnerzy usługi GitHub z klientami mogą pomóc w tworzeniu i konfigurowaniu organizacji, które będą uzyskiwać dostęp do usługi GitHub i identyfikowania administratorów.  Ci Administratorzy otrzymają powiadomienie, że zostały skonfigurowane jako administratorzy.  

Ponieważ ten proces jest bardziej skomplikowany, może upłynąć kilka dni od zakupu subskrypcji dla organizacji i administratorów w pełni skonfigurowany.

Usługa GitHub jest dostępna zarówno jako GitHub.com w chmurze, jak i na lokalnym serwerze usługi GitHub dla przedsiębiorstw.  Procesy zarządzania dwiema wersjami różnią się.  W usłudze GitHub dostępne są różne tematy pomocy i przewodniki administratora ułatwiające zarządzanie subskrypcjami w przedsiębiorstwie usługi GitHub.  Podano linki do wybranych tematów poniżej.  

### <a name="githubcom"></a>GitHub.com 
Aby uzyskać więcej informacji na temat zarządzania GitHub.com, zapoznaj się z następującymi tematami w [pomocy usługi GitHub](https://help.github.com/en).
+ [Pełna lista tematów pomocy](https://help.github.com/en)
+ [Zarządzanie członkostwem w organizacji](https://help.github.com/en/articles/managing-membership-in-your-organization)
+ [Zapraszanie użytkowników do dołączenia do organizacji](https://help.github.com/en/articles/inviting-users-to-join-your-organization)
    - [Usuwanie użytkowników z zespołów/organizacji](https://help.github.com/en/articles/removing-a-member-from-your-organization)
    - [Przywraca dawnemu członkowi organizacji](https://help.github.com/en/articles/reinstating-a-former-member-of-your-organization)
+ [Zarządzanie dostępem przy użyciu ról](https://help.github.com/en/articles/managing-peoples-access-to-your-organization-with-roles)
+ [Organizowanie użytkowników w zespoły](https://help.github.com/en/articles/organizing-members-into-teams)
+ [Zarządzanie dostępem do repozytoriów organizacji](https://help.github.com/en/articles/managing-access-to-your-organizations-repositories)

### <a name="github-enterprise-server"></a>Serwer usługi GitHub Enterprise
Pomoc usługi GitHub zawiera wiele przewodników administratorów, które mogą odpowiedzieć na pytania i zadawać wskazówki dotyczące zarządzania implementacją programu GitHub Enterprise Server w organizacji.

+ [Wyświetl wszystkie przewodniki administratora](https://help.github.com/en/enterprise/2.16/admin)
+ [Zarządzanie użytkownikami](https://help.github.com/en/enterprise/2.16/admin/user-management)
    - [Organizacje i zespoły](https://help.github.com/en/enterprise/2.16/admin/user-management/organizations-and-teams)
        - [Tworzenie organizacji](https://help.github.com/en/enterprise/2.16/admin/user-management/creating-organizations)
        - [Tworzenie zespołów](https://help.github.com/en/enterprise/2.16/admin/user-management/creating-teams)
        - [Dodawanie osób do zespołów](https://help.github.com/en/enterprise/2.16/admin/user-management/adding-people-to-teams)
        - [Usuwanie osób z zespołów i organizacji](https://help.github.com/en/enterprise/2.16/admin/user-management/removing-users-from-teams-and-organizations)
    - [Zabezpieczenia użytkownika](https://help.github.com/en/enterprise/2.16/admin/user-management/user-security)
+ [Instalowanie i Konfigurowanie serwera usługi GitHub Enterprise](https://help.github.com/en/enterprise/2.16/admin/installation)

## <a name="support-resources"></a>Zasoby pomocy technicznej
- Odpowiedzi na pytania dotyczące szerokiej gamy tematów w serwisie GitHub można znaleźć w [pomocy usługi GitHub](https://help.github.com/en).
- Uzyskaj pomoc od innych użytkowników usługi GitHub na [forum społeczności usługi GitHub](https://github.community/).
- Aby uzyskać pomoc dotyczącą sprzedaży, subskrypcji, kont i rozliczeń dla subskrypcji programu Visual Studio, skontaktuj się z [pomocą techniczną subskrypcji](https://visualstudio.microsoft.com/subscriptions/support/)programu Visual Studio.
- Masz pytanie dotyczące środowiska IDE programu Visual Studio, Azure DevOps Services lub innych produktów lub usług Visual Studio?  Odwiedź stronę [pomocy technicznej programu Visual Studio](https://visualstudio.microsoft.com/support/).
- Uzyskaj [Pomoc techniczną](https://support.microsoft.com/en-us/supportforbusiness/productselection?sapId=b77fe80f-5417-80bd-4b2a-275cf0018c24) dla przedsiębiorstw w witrynie GitHub.   

## <a name="next-steps"></a>Następne kroki
Aby uzyskać więcej informacji na temat zarządzania subskrypcjami programu Visual Studio za pomocą usługi GitHub Enterprise, zapoznaj się z [portalem administracyjnym subskrypcji](https://visualstudio.microsoft.com/subscriptions-administration/)programu Visual Studio.
