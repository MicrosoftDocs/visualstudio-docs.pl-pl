---
title: Przygotowanie do publikowania lub wdrażania usługi w chmurze
description: Zapoznaj się z procedurami konfigurowania usług kont w chmurze i magazynu oraz konfigurowania aplikacji platformy Azure.
author: ghogen
manager: jillfra
ms.assetid: 92ee2f9e-ec49-4c7a-900d-620abe5e9d8a
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/10/2017
ms.author: ghogen
ms.openlocfilehash: f6174f8294f3a9e990893ca9a45d77f2a069692e
ms.sourcegitcommit: 59a8732dc563242590f7c6ccf4ced6c6d195533c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81489665"
---
# <a name="prepare-to-publish-or-deploy-a-cloud-service-from-visual-studio"></a>Przygotowywanie do publikowania lub wdrażania usługi w chmurze z programu Visual Studio

Aby opublikować projekt usługi w chmurze, należy skonfigurować następujące usługi zgodnie z opisem w tym artykule:

* **Usługa w chmurze** do uruchamiania ról w środowisku platformy Azure i
* **Konto magazynu,** który zapewnia dostęp do usług obiektów Blob, Queue i Table.

## <a name="create-a-cloud-service"></a>Tworzenie usługi w chmurze

Usługa w chmurze uruchamia swoje role w środowisku platformy Azure. Usługę w chmurze można utworzyć w programie Visual Studio lub za pośrednictwem [witryny Azure portal,](https://portal.azure.com/) zgodnie z opisem w kolejnych sekcjach.

### <a name="create-a-cloud-service-from-visual-studio"></a>Tworzenie usługi w chmurze z programu Visual Studio

1. W ramach wcześniej utworzonego projektu usługi w chmurze kliknij prawym przyciskiem myszy **projekt,** wybierając go.
1. W razie potrzeby zaloguj się za pomocą konta Microsoft lub konta organizacji skojarzonego z subskrypcją platformy Azure, a następnie wybierz pozycję **Dalej,** aby przejść do strony **Ustawienia.**
1. Zostanie wyświetlone okno dialogowe **Utwórz konto usługi w chmurze i magazynu** (jeśli nie, wybierz pozycję **Utwórz nowy** z listy Usługi w **chmurze).**
1. Wprowadź nazwę bez uwzględniania wielkości liter dla usługi w chmurze, która stanowi część adresu URL i musi być unikatowa. Wybierz również grupę regionu lub koligacji i wybierz opcję Replikacja.

### <a name="create-a-cloud-service-through-the-azure-portal"></a>Tworzenie usługi w chmurze za pośrednictwem portalu Azure

1. Zaloguj się w witrynie [Azure Portal](https://portal.azure.com/).
1. Wybierz **usługi w chmurze (klasyczne)** po lewej stronie.
1. Wybierz **+ Dodaj**, a następnie podaj wymagane informacje (nazwa DNS, subskrypcja, grupa zasobów i lokalizacja). Nie jest konieczne przekazywanie pakietu w tym momencie, ponieważ można to zrobić później w programie Visual Studio.
1. Wybierz **pozycję Utwórz,** aby zakończyć proces.

## <a name="create-a-storage-account"></a>Tworzenie konta magazynu

Konto magazynu zapewnia dostęp do usług obiektów Blob, Queue i Table. Konto magazynu można utworzyć za pomocą programu Visual Studio lub [portalu Azure.](https://portal.azure.com/)

### <a name="create-a-storage-account-from-visual-studio"></a>Tworzenie konta magazynu w programie Visual Studio

1. W **Eksploratorze rozwiązań** z wcześniej utworzonym projektem usługi w chmurze znajdź węzeł **Usługi połączone** w projekcie roli, kliknij prawym przyciskiem myszy i wybierz polecenie Dodaj **połączoną usługę**. (W programie Visual Studio 2015 kliknij prawym przyciskiem myszy węzeł **Magazyn** i wybierz polecenie **Utwórz konto magazynu).**
1. Na **wyświetlonej** liście Połączone usługi wybierz pozycję **Cloud Storage with Azure Storage**.
1. W wyświetlonym oknie dialogowym usługi Azure Storage wybierz pozycję **+Utwórz nowe konto magazynu**, w którym pojawi się okno dialogowe, w którym określisz subskrypcję, nazwę konta, warstwę cenową, grupę zasobów i lokalizację.
1. Po zakończeniu wybierz **pozycję Utwórz.** Nowe konto magazynu pojawi się na liście dostępnych kont magazynu w ramach subskrypcji.
1. Wybierz to konto i wybierz pozycję **Dodaj**.

### <a name="create-a-storage-account-through-the-azure-portal"></a>Tworzenie konta magazynu za pośrednictwem witryny Azure portal

1. Zaloguj się w witrynie [Azure Portal](https://portal.azure.com/).
1. Wybierz **+ Nowy** w lewym górnym rogu.
1. Wybierz **magazyn** w obszarze "Azure Marketplace", a następnie **konto usługi Storage — obiekt blob, plik, tabela, kolejka** z prawej strony.
1. Podaj wymagane informacje (nazwa, model wdrażania i tak dalej.
1. Wybierz **pozycję Utwórz,** aby zakończyć proces.

## <a name="configure-your-app-to-use-the-storage-account"></a>Konfigurowanie aplikacji do korzystania z konta magazynu

Po utworzeniu konta magazynu, łączenie się z nim z programu Visual Studio automatycznie aktualizuje konfiguracje usługi dla projektu, w tym adresy URL i klucze dostępu.

Jeśli usługa w chmurze została utworzona z programu Visual Studio przy `ServiceConfiguration.Cloud.cscfg` użyciu `ServiceConfiguration.Local.cscfg`usługi **Dodaj połączoną,** można sprawdzić połączenia, otwierając i .

Jeśli utworzono usługę w chmurze za pośrednictwem witryny Azure portal, wykonaj te same kroki w [Tworzenie konta magazynu z programu Visual Studio,](#create-a-storage-account-from-visual-studio) ale wybierz istniejące konto, a nie tworzenie nowego. Visual Studio następnie aktualizuje konfigurację dla Ciebie.

Aby skonfigurować ustawienia ręcznie, użyj stron właściwości w programie Visual Studio dla odpowiedniej roli w projekcie usługi w chmurze (kliknij prawym przyciskiem myszy rolę i wybierz **polecenie Właściwości).** Aby uzyskać więcej informacji, zobacz [Konfigurowanie ciągu połączenia do konta magazynu](vs-azure-tools-multiple-services-project-configurations.md#configuring-a-connection-string-for-a-storage-account).

### <a name="about-access-keys"></a>Informacje o kluczach dostępu

Portal Azure zawiera adresy URL, których można używać do uzyskiwania dostępu do zasobów w każdej z usług magazynu platformy Azure, a także podstawowe i pomocnicze klucze dostępu dla konta. Te klucze służy do uwierzytelniania żądań złożonych w usługach magazynu.

Pomocniczy klucz dostępu zapewnia taki sam dostęp do konta magazynu jak podstawowy klucz dostępu i jest generowany jako kopia zapasowa w przypadku naruszenia podstawowego klucza dostępu. Ponadto zaleca się regularne ponowne generowanie kluczy dostępu. Można zmodyfikować ustawienie ciągu połączenia, aby użyć klucza pomocniczego podczas ponownego generowania klucza podstawowego, a następnie można go zmodyfikować, aby użyć wygenerowanego klucza podstawowego podczas ponownego generowania klucza pomocniczego.

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej o publikowaniu aplikacji na platformie Azure w programie Visual Studio, zobacz [Publikowanie usługi w chmurze przy użyciu narzędzi platformy Azure](vs-azure-tools-publishing-a-cloud-service.md).
