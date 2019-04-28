---
title: Jak zachować stałej wirtualny adres IP dla usługi w chmurze platformy Azure | Dokumentacja firmy Microsoft
description: Dowiedz się, jak upewnić się, że wirtualny adres IP (VIP) usługi w chmurze platformy Azure nie zmienia się.
author: ghogen
manager: jillfra
assetId: 4a58e2c6-7a79-4051-8a2c-99182ff8b881
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: 525b5fe8f2726ab1f7f2ff80abf7bc06937a7a0b
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62964259"
---
# <a name="retain-a-constant-virtual-ip-address-for-an-azure-cloud-service"></a>Zachowywanie stałego wirtualnego adresu IP usługi w chmurze platformy Azure
Po zaktualizowaniu usługi w chmurze, która jest hostowana na platformie Azure może być konieczne upewnić się, że nie zmienia się wirtualnego adresu IP (VIP) usługi. Wiele usług zarządzania domeny na użytek systemu nazw domen (DNS) rejestracji nazw domen. DNS działa tylko wtedy, gdy adres VIP pozostają bez zmian. Możesz użyć **Kreatora publikacji** w narzędziach platformy Azure, aby upewnić się, że VIP usługi w chmurze nie zmienia się podczas aktualizacji. Aby uzyskać więcej informacji o sposobie zarządzania domeny DNS na użytek usług w chmurze, zobacz [Konfigurowanie niestandardowej nazwy domeny dla usługi w chmurze Azure](/azure/cloud-services/cloud-services-custom-domain-name-portal).

## <a name="publish-a-cloud-service-without-changing-its-vip"></a>Publikowanie usługi w chmurze bez konieczności zmieniania swój adres VIP
Adres VIP usługi w chmurze jest przydzielany przy pierwszym wdrożeniu jej na platformie Azure w konkretnym środowisku, takie jak w środowisku produkcyjnym. Wirtualne adresy IP zmienia się tylko wtedy, gdy jawnie Usuń wdrożenie lub wdrożenie jest niejawnie usunięte przez proces wdrażania aktualizacji. Aby zachować adres VIP, nie należy usunąć wdrożenie, a następnie należy się upewnić, że program Visual Studio nie powoduje usunięcia automatycznie wdrożenia. 

Możesz określić ustawienia wdrażania **Kreatora publikacji**, która obsługuje kilka opcji wdrażania. Można określić świeże wdrożenie lub wdrożenie aktualizacji, może być przyrostowych lub jednocześnie. Oba rodzaje wdrożenia aktualizacji zachować adres VIP. Uzyskać definicje tych różnych typów wdrożenia, zobacz [Kreator publikowania aplikacji Azure](vs-azure-tools-publish-azure-application-wizard.md). Ponadto możesz kontrolować, czy usuwany jest poprzedniego wdrożenia usługi w chmurze, jeśli wystąpi błąd. Jeśli ta opcja nie ustawione poprawnie, adres VIP może ulegać nieoczekiwanym zmianom.

## <a name="update-a-cloud-service-without-changing-its-vip"></a>Aktualizowanie usługi w chmurze bez konieczności zmieniania swój adres VIP
1. Utwórz lub Otwórz projekt usługi w chmurze platformy Azure w programie Visual Studio. 

2. W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy projekt. W menu skrótów wybierz **Publikuj**.

    ![Menu publikowania](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/solution-explorer-publish-menu.png)

3. W **publikowanie aplikacji platformy Azure** okna dialogowego Wybierz subskrypcję platformy Azure, do której chcesz wdrożyć. Zarejestruj się, jeśli to konieczne i wybierz pozycję **dalej**.

    ![Publikowanie usługi Azure Application stronę logowania](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-signin.png)

4. Na **typowe ustawienia** kartę, upewnij się, że nazwę chmury usługi jest wdrażany, **środowiska**, **konfigurację kompilacji**i **Konfiguracji usługi** są poprawne.

    ![Publikowanie kartę wspólne ustawienia aplikacji platformy Azure](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-common-settings.png)

5. Na **Zaawansowane ustawienia** kartę, upewnij się, że **drażania** i **konta magazynu** są poprawne. Upewnij się, że **Usuń wdrożenie w przypadku niepowodzenia** pole wyboru jest wyczyszczone, a następnie upewnij się, że **wdrożenia aktualizacji** pole wyboru jest zaznaczone. Przez wyczyszczenie **Usuń wdrożenie w przypadku niepowodzenia** pole wyboru, należy upewnić się czy VIP nie jest utracone, jeśli wystąpi błąd podczas wdrażania. Wybierając **wdrożenia aktualizacji** pole wyboru, możesz upewnij się, że wdrożenie nie jest usuwany VIP nie jest utracone po ponownym opublikowaniu aplikacji. 

    ![Publikowanie kartę Zaawansowane ustawienia aplikacji platformy Azure](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-advanced-settings.png)

6. Aby bardziej szczegółowo określić, jak chcesz, aby role do zaktualizowania, wybierz pozycję **ustawienia** obok **wdrożenia aktualizacji**. Wybierz opcję **aktualizacji przyrostowej** lub **jednoczesne aktualizowanie**i wybierz **OK**. Wybierz **aktualizacji przyrostowej** można zaktualizować każde wystąpienie aplikacji, po kolei, dlatego, że aplikacja jest zawsze dostępna. Wybierz **jednoczesne aktualizowanie** do zaktualizowania wszystkich wystąpień aplikacji w tym samym czasie. Jednoczesne aktualizowanie jest szybsze, ale usługa może nie być dostępna podczas procesu aktualizacji. Gdy skończysz, wybierz pozycję **dalej**.

    ![Publikowanie strony Ustawienia wdrażania aplikacji platformy Azure](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-deployment-update-settings.png)

7. W **publikowanie aplikacji platformy Azure** okno dialogowe, wybierz opcję **dalej** aż **Podsumowanie** zostanie wyświetlona strona. Sprawdź ustawienia, a następnie wybierz **Publikuj**.

    ![Publikowanie strony Podsumowanie aplikacji platformy Azure](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-summary.png)

## <a name="next-steps"></a>Następne kroki
- [Za pomocą programu Visual Studio Azure Kreatorze publikacji aplikacji](vs-azure-tools-publish-azure-application-wizard.md)
