---
title: Uzyskiwanie dostępu do maszyn wirtualnych platformy Azure z poziomu Eksploratora serwera | Dokumentacja firmy Microsoft
description: Pobierz omówienie sposobu wyświetlania tworzenie i zarządzanie nimi maszyn wirtualnych (VM) w Eksploratorze serwera w programie Visual Studio.
author: ghogen
manager: jillfra
assetId: eb3afde6-ba90-4308-9ac1-3cc29da4ede0
ms.prod: visual-studio-dev14
ms.technology: vs-azure
ms.custom: vs-azure
ms.workload: azure-vs
ms.topic: conceptual
ms.date: 8/31/2017
ms.author: ghogen
ms.openlocfilehash: 6d6b35218355db686a4154928e5529d213e733d5
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54779697"
---
# <a name="accessing-azure-virtual-machines-from-server-explorer"></a>Uzyskiwanie dostępu do maszyn wirtualnych platformy Azure z poziomu Eksploratora serwera

W przypadku maszyn wirtualnych hostowanych na platformie Azure można uzyskiwać do nich dostęp w Eksploratorze serwera. Należy najpierw zalogować do subskrypcji platformy Azure do wyświetlenia w usługach mobilnych. Aby zalogować, otwórz menu skrótów dla węzła platformy Azure w Eksploratorze serwera, a następnie wybierz **Połącz platformę Microsoft Azure**.

1. W programie Cloud Explorer wybierz maszynę wirtualną, a następnie wybierz klawisz F4, aby wyświetlić okno właściwości.

    W poniższej tabeli przedstawiono, jakie właściwości są dostępne, ale są one wszystkie tylko do odczytu. Aby je zmienić, należy użyć [witryny Azure portal](http://go.microsoft.com/fwlink/p/?LinkID=525040).

   | Właściwość | Opis |
   | --- | --- |
   | Nazwa DNS |Adres URL przy użyciu adresu internetowego maszyny wirtualnej. |
   | Środowisko |Dla maszyny wirtualnej wartość tej właściwości jest zawsze produkcji. |
   | Nazwa |Nazwa maszyny wirtualnej. |
   | Rozmiar |Rozmiar maszyny wirtualnej, która odzwierciedla ilość pamięci i miejsca na dysku, który jest dostępny. Aby uzyskać więcej informacji, zobacz [rozmiarów maszyn wirtualnych](https://docs.microsoft.com/azure/cloud-services/cloud-services-sizes-specs). |
   | Stan |Wartości obejmują uruchamianie, uruchomiono, zatrzymywania, zatrzymane i pobierania stanu. Jeśli pojawi się stan pobierania, bieżący stan jest nieznany. Wartości dla tej właściwości różnią się od wartości, które są używane na [witryny Azure portal](http://go.microsoft.com/fwlink/p/?LinkID=525040). |
   | Identyfikator subskrypcji |Identyfikator subskrypcji dla Twojego konta platformy Azure. Te informacje można wyświetlić na [witryny Azure portal](http://go.microsoft.com/fwlink/p/?LinkID=525040) , wyświetlając właściwości dla subskrypcji. |
2. Wybierz węzeł punktu końcowego, a następnie wyświetlić **właściwości** okna.
3. W poniższej tabeli opisano dostępne właściwości punktów końcowych, ale są one tylko do odczytu. Aby dodać lub edytować punkty końcowe dla maszyny wirtualnej, należy użyć [witryny Azure portal](http://go.microsoft.com/fwlink/p/?LinkID=525040). 

   | Właściwość | Opis |
   | --- | --- |
   | Nazwa |Identyfikator punktu końcowego. |
   | Port prywatny |Port dostępu do sieci wewnętrznej do aplikacji. |
   | Protokół |Protokół, który korzysta z warstwy transportowej dla tego punktu końcowego, TCP lub UDP. |
   | Port publiczny |Port używany dla publicznego dostępu do aplikacji. |
