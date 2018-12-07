---
title: Przygotowywanie do opublikowania lub wdrożyć usługę w chmurze
description: Dowiedz się procedury konfigurowania chmura i magazyn usługi kont i konfigurowanie aplikacji systemu Azure.
author: ghogen
manager: douge
ms.assetid: 92ee2f9e-ec49-4c7a-900d-620abe5e9d8a
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 11/10/2017
ms.author: ghogen
ms.openlocfilehash: 4b0ac752e65530d98b680d7e2e4a9095639423e7
ms.sourcegitcommit: 708f77071c73c95d212645b00fa943d45d35361b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/07/2018
ms.locfileid: "53063349"
---
# <a name="prepare-to-publish-or-deploy-a-cloud-service-from-visual-studio"></a>Przygotowywanie do publikowania lub wdrażania usługi w chmurze z programu Visual Studio

Aby opublikować projekt usługi w chmurze, możesz skonfigurować następujące usługi zgodnie z opisem w tym artykule:

* A **usługi w chmurze** do uruchamiania roli w środowisku platformy Azure i
* A **konta magazynu** , który zapewnia dostęp do usług obiektów Blob, kolejek i tabel.

## <a name="create-a-cloud-service"></a>Utwórz usługę w chmurze

Usługa w chmurze działa role w środowisku platformy Azure. Można utworzyć usługi w chmurze w programie Visual Studio lub za pomocą [witryny Azure portal](https://portal.azure.com/) zgodnie z opisem w kolejnych sekcjach.

### <a name="create-a-cloud-service-from-visual-studio"></a>Utwórz usługę w chmurze w programie Visual Studio

1. Przy użyciu utworzonego wcześniej projektu usługi w chmurze, kliknij prawym przyciskiem myszy wybierz projekt **Publikuj**.
1. Jeśli to konieczne, zaloguj się przy użyciu Microsoft lub konta organizacyjnego skojarzonego z subskrypcją platformy Azure, a następnie wybierz **dalej** celu przechodzenia do **ustawienia** strony.
1. A **tworzenia usługi w chmurze i konto magazynu** zostanie wyświetlone okno dialogowe (Jeśli nie, wybierz **Utwórz nowy** z **usługi w chmurze** listy).
1. Wprowadź nazwę bez uwzględniania wielkości liter dla usługi w chmurze, która jest częścią adresu URL i musi być unikatowa. Ponadto wybierz Region lub grupa koligacji, a następnie wybierz opcję replikacji.

### <a name="create-a-cloud-service-through-the-azure-portal"></a>Utwórz usługę w chmurze za pośrednictwem witryny Azure portal

1. Zaloguj się do [witryny Azure portal](https://portal.azure.com/).
1. Wybierz **usług w chmurze (klasyczne)** w lewej części strony.
1. Wybierz **+ Dodaj**, następnie podaj wymagane informacje (nazwa DNS, subskrypcji, grupy zasobów i lokalizacji). Nie jest niezbędne do przekazania pakietu na tym etapie, ponieważ możesz zrobić to później w programie Visual Studio.
1. Wybierz **Utwórz** aby ukończyć proces.

## <a name="create-a-storage-account"></a>Tworzenie konta magazynu

Konto magazynu zapewnia dostęp do usług obiektów Blob, kolejek i tabel. Można utworzyć konta magazynu za pomocą programu Visual Studio lub [witryny Azure portal](https://portal.azure.com/).

### <a name="create-a-storage-account-from-visual-studio"></a>Tworzenie konta magazynu w programie Visual Studio

1. W **Eksploratora rozwiązań** przy użyciu utworzonego wcześniej projektu usługi w chmurze, zlokalizuj **podłączone usługi** węzeł w projekcie roli, kliknij prawym przyciskiem myszy i wybierz **Dodaj podłączoną usługę**. (W programie Visual Studio 2015, kliknij prawym przyciskiem myszy **magazynu** a następnie wybierz węzeł **Utwórz konto magazynu**.)
1. W **podłączone usługi** wyświetlonej listy wybierz **magazynu w chmurze z usługą Azure Storage**.
1. W oknie dialogowym usługi Azure Storage, która pojawia się, zaznaczyć **+ Utwórz nowe konto magazynu**, która wyświetla okno dialogowe umożliwiające wybór subskrypcji, nazwę fo konta, cen warstwy, grupy zasobów i lokalizacji.
1. Wybierz **Utwórz** po zakończeniu. Nowe konto magazynu zostanie wyświetlona na liście kont magazynu dostępnych w ramach subskrypcji.
1. Wybierz konto, a następnie zaznacz **Dodaj**.

### <a name="create-a-storage-account-through-the-azure-portal"></a>Tworzenie konta magazynu w witrynie Azure portal

1. Zaloguj się do [witryny Azure portal](https://portal.azure.com/).
1. Wybierz **+ nowy** w lewym górnym rogu.
1. Wybierz **magazynu** w obszarze "Azure Marketplace," następnie **konto magazynu — obiektów blob, plik, tabela, kolejka** z prawej strony.
1. Podaj wymagane informacje (nazwa, model wdrożenia i tak dalej.
1. Wybierz **Utwórz** aby ukończyć proces.

## <a name="configure-your-app-to-use-the-storage-account"></a>Skonfiguruj aplikację, aby użyć konta magazynu

Po utworzeniu konta magazynu, nawiązania z nim w programie Visual Studio automatycznie aktualizuje konfiguracje usługi dla projektu, w tym adresy URL i klucze dostępu.

Jeśli usługa w chmurze utworzone z programu Visual Studio przy użyciu **Dodaj podłączoną usługę**, połączenia można sprawdzić, otwierając `ServiceConfiguration.Cloud.cscfg` i `ServiceConfiguration.Local.cscfg`.

Jeśli utworzono usługi w chmurze za pośrednictwem witryny Azure portal, wykonaj te same czynności w [Tworzenie konta magazynu w programie Visual Studio](#create-a-storage-account-from-visual-studio) , ale wybierz istniejące konto, zamiast tworzenia nowej. Program Visual Studio następnie aktualizuje konfigurację dla Ciebie.

Aby skonfigurować ustawienia ręcznie, używać stron właściwości w programie Visual Studio na zastosowanie roli w projekt usługi w chmurze (kliknij prawym przyciskiem myszy rolę, a następnie wybierz pozycję **właściwości**). Aby uzyskać więcej informacji, zobacz [Konfigurowanie parametrów połączenia z kontem magazynu](vs-azure-tools-multiple-services-project-configurations.md#configuring-a-connection-string-for-a-storage-account).

### <a name="about-access-keys"></a>Klawisze dostępu — informacje

Witryna Azure portal zawiera adresy URL, w której można uzyskać dostęp do zasobów we wszystkich usług Azure storage, a także klucze podstawowe i pomocnicze dostępu dla konta. Używasz tych kluczy do uwierzytelniania żądania skierowanego do usługi magazynu.

Pomocniczy klucz dostępu zapewnia taki sam dostęp do swojego konta magazynu jako podstawowy klucz dostępu i jest generowany jako kopia zapasowa powinna naruszony klucz dostępu. Ponadto zaleca się ponowne generowanie kluczy dostępu w regularnych odstępach czasu. Można zmodyfikować ustawienie parametrów połączenia, aby używać klucza pomocniczego, podczas ponownego generowania klucza podstawowego, a następnie zmodyfikować, aby użyć wygenerowano ponownie klucz podstawowy, podczas ponownego generowania klucza pomocniczego.

## <a name="next-steps"></a>Następne kroki

Aby dowiedzieć się więcej na temat publikowania aplikacji na platformie Azure z programu Visual Studio, zobacz [publikowania usługi w chmurze przy użyciu narzędzi Azure](vs-azure-tools-publishing-a-cloud-service.md).
