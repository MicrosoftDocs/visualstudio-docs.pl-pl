---
title: Zachowywanie stałego wirtualnego adresu IP dla usługi w chmurze platformy Azure
description: Dowiedz się, jak upewnić się, że wirtualny adres IP (VIP) usługi w chmurze platformy Azure nie zmienia się.
ms.custom: vs-azure
author: ghogen
manager: jillfra
assetId: 4a58e2c6-7a79-4051-8a2c-99182ff8b881
ms.workload: azure-vs
ms.topic: how-to
ms.date: 03/21/2017
ms.author: ghogen
ms.openlocfilehash: 0ebd709e77e88ef1ed81b6a01735a5eed5be7508
ms.sourcegitcommit: 4ae5e9817ad13edd05425febb322b5be6d3c3425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2020
ms.locfileid: "90035953"
---
# <a name="retain-a-constant-virtual-ip-address-for-an-azure-cloud-service"></a>Zachowywanie stałego wirtualnego adresu IP usługi w chmurze platformy Azure
W przypadku aktualizowania usługi w chmurze hostowanej na platformie Azure może być konieczne zagwarantowanie, że wirtualny adres IP (VIP) usługi nie jest zmieniany. Wiele usług zarządzania domenami używa systemu nazw domen (DNS) do rejestrowania nazw domen. DNS działa tylko wtedy, gdy adres VIP pozostaje taki sam. Możesz użyć **Kreatora publikacji** w narzędziach platformy Azure, aby upewnić się, że wirtualne adresy IP usługi w chmurze nie ulegają zmianie po ich aktualizacji. Aby uzyskać więcej informacji na temat korzystania z zarządzania domeną DNS dla usług w chmurze, zobacz [Konfigurowanie niestandardowej nazwy domeny dla usługi w chmurze platformy Azure](/azure/cloud-services/cloud-services-custom-domain-name-portal).

## <a name="publish-a-cloud-service-without-changing-its-vip"></a>Publikowanie usługi w chmurze bez zmiany adresu VIP
Adres VIP usługi w chmurze jest przypisywany podczas pierwszego wdrożenia na platformie Azure w konkretnym środowisku, na przykład w środowisku produkcyjnym. Adres VIP zostanie zmieniony tylko wtedy, gdy usuniesz wdrożenie jawnie lub wdrożenie zostanie niejawnie usunięte przez proces aktualizacji wdrożenia. Aby zachować adres VIP, nie należy usuwać wdrożenia i należy upewnić się, że program Visual Studio nie usuwa wdrożenia automatycznie.

Ustawienia wdrożenia można określić w **Kreatorze publikacji**, który obsługuje kilka opcji wdrażania. Możesz określić nowe wdrożenie lub wdrożenie aktualizacji, które może być przyrostowe lub jednoczesne. Oba rodzaje wdrożenia aktualizacji zachowują adres VIP. Aby zapoznać się z definicjami różnych typów wdrożenia, zobacz [Kreator publikowania aplikacji platformy Azure](vs-azure-tools-publish-azure-application-wizard.md). Ponadto można kontrolować, czy poprzednie wdrożenie usługi w chmurze zostało usunięte w przypadku wystąpienia błędu. Jeśli ta opcja nie zostanie ustawiona poprawnie, adres VIP może ulec zmianie nieoczekiwanie.

## <a name="update-a-cloud-service-without-changing-its-vip"></a>Aktualizowanie usługi w chmurze bez zmiany adresu VIP
1. Utwórz lub Otwórz projekt usługi w chmurze platformy Azure w programie Visual Studio.

2. W **Eksplorator rozwiązań**kliknij prawym przyciskiem myszy projekt. W menu skrótów wybierz pozycję **Publikuj**.

    ![Menu Publikuj](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/solution-explorer-publish-menu.png)

3. W oknie dialogowym **publikowanie aplikacji platformy Azure** wybierz subskrypcję platformy Azure, w której chcesz przeprowadzić wdrożenie. W razie potrzeby zaloguj się, a następnie wybierz przycisk **dalej**.

    ![Publikowanie strony logowania aplikacji platformy Azure](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-signin.png)

4. Na karcie **typowe ustawienia** Sprawdź, czy nazwa usługi w chmurze, która jest wdrażana, **środowisko**, **Konfiguracja kompilacji**i **Konfiguracja usługi** są poprawne.

    ![Karta Publikowanie ustawień wspólnych aplikacji platformy Azure](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-common-settings.png)

5. Na karcie **Ustawienia zaawansowane** Sprawdź, czy **etykieta wdrożenia** i **konto magazynu** są poprawne. Upewnij się, że pole wyboru **Usuń wdrożenie w przypadku niepowodzenia** jest zaznaczone, i sprawdź, czy pole wyboru **Aktualizacja wdrożenia** jest wybrane. Usuwając zaznaczenie pola wyboru **Usuń wdrożenie przy niepowodzeniem** , upewnij się, że adres VIP nie zostanie utracony w przypadku wystąpienia błędu podczas wdrażania. Zaznaczając pole wyboru **Aktualizacja wdrożenia** , upewnij się, że wdrożenie nie zostanie usunięte i że adres VIP nie zostanie utracony po ponownym opublikowaniu aplikacji.

    ![Karta Publikowanie ustawień zaawansowanych aplikacji platformy Azure](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-advanced-settings.png)

6. Aby dalej określić, w jaki sposób mają być aktualizowane role, wybierz pozycję **Ustawienia** obok pozycji **Aktualizacja wdrożenia**. Wybierz opcję **aktualizacja przyrostowa** lub **równoczesna aktualizacja**, a następnie wybierz **przycisk OK**. Wybierz pozycję **aktualizacja przyrostowa** , aby zaktualizować każde wystąpienie aplikacji, jedno po drugim, aby aplikacja była zawsze dostępna. Wybierz **jednoczesne aktualizacje** , aby zaktualizować wszystkie wystąpienia aplikacji w tym samym czasie. Jednoczesne aktualizowanie jest szybsze, ale usługa może być niedostępna w trakcie procesu aktualizacji. Gdy skończysz, wybierz pozycję **dalej**.

    ![Strona Publikowanie ustawień wdrożenia aplikacji platformy Azure](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-deployment-update-settings.png)

7. W oknie dialogowym **publikowanie aplikacji platformy Azure** wybierz pozycję **dalej** , dopóki nie zostanie wyświetlona strona **Podsumowanie** . Sprawdź ustawienia, a następnie wybierz pozycję **Publikuj**.

    ![Strona publikowania podsumowania aplikacji platformy Azure](./media/vs-azure-tools-cloud-service-retain-a-constant-virtual-ip-address/azure-publish-summary.png)

## <a name="next-steps"></a>Następne kroki
- [Korzystanie z kreatora publikacji aplikacji platformy Azure programu Visual Studio](vs-azure-tools-publish-azure-application-wizard.md)
