---
title: Uzyskiwanie dostępu do usługi Azure Virtual Machines z Eksplorator serwera | Microsoft Docs
description: Omówienie sposobu wyświetlania tworzenia maszyn wirtualnych platformy Azure i zarządzania nimi w usłudze Eksplorator serwera w Visual Studio.
author: ghogen
manager: jmartens
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/31/2017
ms.author: ghogen
ms.openlocfilehash: f95542c79e6f8cde83866caa082b8e025b069589
ms.sourcegitcommit: 690bfc20744e4b543ee81030a60c8fc6d0d6610f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/29/2021
ms.locfileid: "113038580"
---
# <a name="accessing-azure-virtual-machines-from-server-explorer"></a>Uzyskiwanie dostępu do maszyn wirtualnych platformy Azure z poziomu Eksploratora serwera

::: moniker range=">=vs-2022"
> [!Important]
> Węzeł usługi Azure Eksplorator serwera został wycofany w Visual Studio 2022 r. Możesz użyć witryny Azure Portal lub nadal korzystać z węzła platformy Azure Eksplorator serwera w poprzednich wersjach Visual Studio.
>
> Ponadto [Eksplorator usługi Microsoft Azure Storage](/azure/vs-azure-tools-storage-manage-with-storage-explorer) to bezpłatna, autonomiczna aplikacja firmy Microsoft. Można jej używać do wizualnej pracy z danymi usługi Azure Storage w systemach Windows, macOS i Linux.
>
> Aby uzyskać więcej informacji o Visual Studio 2022 r., zobacz informacje [o wersji](/visualstudio/releases/2022/release-notes-preview/).

::: moniker-end

::: moniker range="<=vs-2019"

Jeśli masz maszyny wirtualne hostowane na platformie Azure, możesz uzyskać do nich dostęp w Eksplorator serwera. Aby wyświetlić usługi mobilne, musisz najpierw zalogować się do subskrypcji platformy Azure. Aby się zalogować, otwórz menu skrótów dla węzła platformy Azure w usłudze Eksplorator serwera, a następnie wybierz pozycję Połącz z **Microsoft Azure**.

1. W Eksploratorze chmury wybierz maszynę wirtualną, a następnie naciśnij klawisz F4, aby wyświetlić okno właściwości.

    W poniższej tabeli przedstawiono dostępne właściwości, ale wszystkie są tylko do odczytu. Aby je zmienić, użyj [Azure Portal](https://portal.azure.com).

   | Właściwość | Opis |
   | --- | --- |
   | Nazwa DNS |Adres URL z adresem internetowym maszyny wirtualnej. |
   | Środowisko |W przypadku maszyny wirtualnej wartość tej właściwości to zawsze Produkcja. |
   | Nazwa |Nazwa maszyny wirtualnej. |
   | Rozmiar |Rozmiar maszyny wirtualnej, który odzwierciedla ilość dostępnej pamięci i miejsca na dysku. Aby uzyskać więcej informacji, zobacz [Virtual Machine Sizes (Rozmiary maszyn wirtualnych).](/azure/cloud-services/cloud-services-sizes-specs) |
   | Stan |Wartości obejmują uruchamianie, uruchamianie, zatrzymywanie, zatrzymywanie i pobieranie stanu. Jeśli zostanie wyświetlony stan Pobieranie, bieżący stan jest nieznany. Wartości tej właściwości różnią się od wartości używanych w Azure Portal [.](https://portal.azure.com) |
   | Subscriptionid |Identyfikator subskrypcji dla konta platformy Azure. Te informacje można wyświetlić na stronie [Azure Portal,](https://portal.azure.com) wyświetlając właściwości subskrypcji. |
2. Wybierz węzeł punktu końcowego, a następnie wyświetl **okno** Właściwości.
3. W poniższej tabeli opisano dostępne właściwości punktów końcowych, ale są one tylko do odczytu. Aby dodać lub edytować punkty końcowe dla maszyny wirtualnej, użyj [Azure Portal](https://portal.azure.com).

   | Właściwość | Opis |
   | --- | --- |
   | Nazwa |Identyfikator punktu końcowego. |
   | Port prywatny |Port wewnętrznego dostępu sieciowego do aplikacji. |
   | Protokół |Protokół używany przez warstwę transportu dla tego punktu końcowego : TCP lub UDP. |
   | Port publiczny |Port używany do publicznego dostępu do aplikacji. |

::: moniker-end