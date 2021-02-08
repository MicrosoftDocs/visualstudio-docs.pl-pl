---
title: Przygotowanie do opublikowania lub wdrożenia usługi w chmurze
description: Zapoznaj się z procedurami konfigurowania usług w chmurze i konta magazynu oraz konfigurowania aplikacji platformy Azure.
author: ghogen
manager: jmartens
ms.workload: azure-vs
ms.topic: how-to
ms.date: 11/10/2017
ms.author: ghogen
ms.openlocfilehash: 06157f1476762af5bfe24ce950e29e80ac60e6b1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99844427"
---
# <a name="prepare-to-publish-or-deploy-a-cloud-service-from-visual-studio"></a>Przygotowywanie do publikowania lub wdrażania usługi w chmurze z programu Visual Studio

Aby opublikować projekt usługi w chmurze, należy skonfigurować następujące usługi zgodnie z opisem w tym artykule:

* **Usługa w chmurze** służąca do uruchamiania ról w środowisku platformy Azure, a
* **Konto magazynu** , które zapewnia dostęp do usług obiektów blob, kolejek i tabel.

## <a name="create-a-cloud-service"></a>Tworzenie usługi w chmurze

Usługa w chmurze uruchamia Twoje role w środowisku platformy Azure. Usługę w chmurze można utworzyć w programie Visual Studio lub za pomocą [Azure Portal](https://portal.azure.com/) zgodnie z opisem w poniższych sekcjach.

### <a name="create-a-cloud-service-from-visual-studio"></a>Tworzenie usługi w chmurze w programie Visual Studio

1. W przypadku utworzonego wcześniej projektu usługi w chmurze kliknij prawym przyciskiem myszy projekt, a następnie wybierz pozycję **Publikuj**.
1. W razie potrzeby zaloguj się przy użyciu konta Microsoft lub organizacji skojarzonego z subskrypcją platformy Azure, a następnie wybierz pozycję **dalej** , aby przejść do strony **ustawień** .
1. Zostanie wyświetlone okno dialogowe **Tworzenie usługi w chmurze i konta magazynu** (jeśli nie, wybierz pozycję **Utwórz nowy** na liście **usługi w chmurze** ).
1. Wprowadź nazwę bez uwzględniania wielkości liter dla usługi w chmurze, która stanowi część adresu URL i musi być unikatowa. Wybierz również region lub grupę koligacji, a następnie wybierz opcję replikacji.

### <a name="create-a-cloud-service-through-the-azure-portal"></a>Tworzenie usługi w chmurze za pomocą Azure Portal

1. Zaloguj się w witrynie [Azure Portal](https://portal.azure.com/).
1. Wybierz pozycję **Cloud Services (klasyczny)** w lewej części strony.
1. Wybierz pozycję **+ Dodaj**, a następnie podaj wymagane informacje (nazwa DNS, subskrypcja, Grupa zasobów i lokalizacja). Nie jest konieczne przekazywanie pakietu w tym momencie, ponieważ w dalszej części programu Visual Studio.
1. Wybierz pozycję **Utwórz** , aby ukończyć proces.

## <a name="create-a-storage-account"></a>Tworzenie konta magazynu

Konto magazynu zapewnia dostęp do usług obiektów blob, kolejek i tabel. Konto magazynu można utworzyć za pomocą programu Visual Studio lub [Azure Portal](https://portal.azure.com/).

### <a name="create-a-storage-account-from-visual-studio"></a>Tworzenie konta magazynu z poziomu programu Visual Studio

1. W **Eksplorator rozwiązań** z wcześniej utworzonym projektem usługi w chmurze zlokalizuj węzeł **usługi połączone** w ramach projektu roli, kliknij prawym przyciskiem myszy i wybierz polecenie **Dodaj podłączoną usługę**. (W programie Visual Studio 2015 kliknij prawym przyciskiem myszy węzeł **Magazyn** , a następnie wybierz pozycję **Utwórz konto magazynu**).
1. Na wyświetlonej liście **usługi połączone** wybierz pozycję **Magazyn w chmurze z usługą Azure Storage**.
1. W wyświetlonym oknie dialogowym usługi Azure Storage wybierz pozycję **+ Utwórz nowe konto magazynu**, co spowoduje wyświetlenie okna dialogowego, w którym można określić subskrypcję, nazwę konta, warstwę cenową, grupę zasobów i lokalizację.
1. Po zakończeniu wybierz pozycję **Utwórz** . Nowe konto magazynu zostanie wyświetlone na liście dostępnych kont magazynu w ramach subskrypcji.
1. Wybierz to konto i wybierz pozycję **Dodaj**.

### <a name="create-a-storage-account-through-the-azure-portal"></a>Tworzenie konta magazynu za pomocą Azure Portal

1. Zaloguj się w witrynie [Azure Portal](https://portal.azure.com/).
1. Wybierz pozycję **+ Nowy** w lewym górnym rogu.
1. Wybierz pozycję **Magazyn** w obszarze "Azure Marketplace", a następnie kliknij pozycję **konto magazynu — obiekt BLOB, plik, tabela, kolejka** po prawej stronie.
1. Podaj wymagane informacje (nazwę, model wdrażania i tak dalej.
1. Wybierz pozycję **Utwórz** , aby ukończyć proces.

## <a name="configure-your-app-to-use-the-storage-account"></a>Konfigurowanie aplikacji do korzystania z konta magazynu

Po utworzeniu konta magazynu połączenie z nim w programie Visual Studio automatycznie aktualizuje konfiguracje usługi dla projektu, w tym adresy URL i klucze dostępu.

Jeśli utworzono usługę w chmurze z poziomu programu Visual Studio przy użyciu opcji **Dodaj podłączoną usługę**, możesz sprawdzić połączenia, otwierając `ServiceConfiguration.Cloud.cscfg` i `ServiceConfiguration.Local.cscfg` .

Jeśli usługa w chmurze została utworzona za pośrednictwem Azure Portal, wykonaj te same czynności w temacie [Tworzenie konta magazynu w programie Visual Studio](#create-a-storage-account-from-visual-studio) , ale zamiast tworzenia nowego konta wybierz istniejące konto. Program Visual Studio następnie aktualizuje konfigurację.

Aby skonfigurować ustawienia ręcznie, użyj stron właściwości w programie Visual Studio, aby uzyskać odpowiednią rolę w projekcie usługi w chmurze (kliknij prawym przyciskiem myszy rolę i wybierz polecenie **Właściwości**). Aby uzyskać więcej informacji, zobacz [Konfigurowanie parametrów połączenia na koncie magazynu](vs-azure-tools-multiple-services-project-configurations.md#configuring-a-connection-string-for-a-storage-account).

### <a name="about-access-keys"></a>Informacje o kluczach dostępu

W Azure Portal przedstawiono adresy URL, których można użyć w celu uzyskania dostępu do zasobów w każdej z usług Azure Storage, a także podstawowy i pomocniczy klucz dostępu dla Twojego konta. Te klucze są używane do uwierzytelniania żądań wykonywanych względem usług magazynu.

Pomocniczy klucz dostępu zapewnia ten sam dostęp do konta magazynu jako podstawowy klucz dostępu i jest generowany jako kopia zapasowa, jeśli podstawowy klucz dostępu zostanie naruszony. Ponadto zaleca się regularne ponowne generowanie kluczy dostępu. Możesz zmodyfikować ustawienie parametrów połączenia, aby użyć klucza pomocniczego podczas ponownego generowania klucza podstawowego, a następnie można go zmodyfikować, aby używał ponownie wygenerowanego klucza podstawowego podczas ponownego generowania klucza pomocniczego.

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej o publikowaniu aplikacji na platformie Azure z poziomu programu Visual Studio, zobacz [publikowanie usługi w chmurze przy użyciu narzędzi platformy Azure](vs-azure-tools-publishing-a-cloud-service.md).
