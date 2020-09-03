---
title: Uzyskiwanie dostępu do usługi Azure Virtual Machines z Eksplorator serwera | Microsoft Docs
description: Zapoznaj się z omówieniem tworzenia maszyn wirtualnych platformy Azure w Eksplorator serwera w programie Visual Studio i zarządzania nimi.
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
ms.openlocfilehash: f4c1ff547d9d550cbbc2e77435b159543fc16bf6
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "75917094"
---
# <a name="accessing-azure-virtual-machines-from-server-explorer"></a>Uzyskiwanie dostępu do maszyn wirtualnych platformy Azure z poziomu Eksploratora serwera

Jeśli masz maszyny wirtualne hostowane przez platformę Azure, możesz uzyskać do nich dostęp w Eksplorator serwera. Musisz najpierw zalogować się do subskrypcji platformy Azure, aby wyświetlić swoje usługi mobilne. Aby się zalogować, otwórz menu skrótów dla węzła platformy Azure w Eksplorator serwera i wybierz polecenie **Połącz z Microsoft Azure**.

1. W programie Cloud Explorer wybierz maszynę wirtualną, a następnie wybierz klawisz F4, aby wyświetlić okno właściwości.

    W poniższej tabeli przedstawiono właściwości dostępne, ale są one tylko do odczytu. Aby je zmienić, użyj [Azure Portal](https://portal.azure.com/).

   | Właściwość | Opis |
   | --- | --- |
   | Nazwa DNS |Adres URL z adresem internetowym maszyny wirtualnej. |
   | Środowisko |Dla maszyny wirtualnej wartość tej właściwości jest zawsze produkcja. |
   | Nazwa |Nazwa maszyny wirtualnej. |
   | Rozmiar |Rozmiar maszyny wirtualnej, który odzwierciedla ilość dostępnej pamięci i miejsca na dysku. Aby uzyskać więcej informacji, zobacz [rozmiary maszyn wirtualnych](/azure/cloud-services/cloud-services-sizes-specs). |
   | Stan |Wartości obejmują uruchamianie, uruchamianie, zatrzymywanie, zatrzymanie i pobieranie stanu. Jeśli zostanie wyświetlony stan pobieranie, bieżący stan jest nieznany. Wartości tej właściwości różnią się od wartości, które są używane w [Azure Portal](https://portal.azure.com/). |
   | Identyfikator |Identyfikator subskrypcji Twojego konta platformy Azure. Te informacje można wyświetlić na [Azure Portal](https://portal.azure.com/) , wyświetlając właściwości subskrypcji. |
2. Wybierz węzeł punktu końcowego, a następnie Wyświetl okno **Właściwości** .
3. W poniższej tabeli opisano dostępne właściwości punktów końcowych, ale są one tylko do odczytu. Aby dodać lub edytować punkty końcowe dla maszyny wirtualnej, użyj [Azure Portal](https://portal.azure.com/). 

   | Właściwość | Opis |
   | --- | --- |
   | Nazwa |Identyfikator punktu końcowego. |
   | Port prywatny |Port wewnętrznego dostępu do sieci dla aplikacji. |
   | Protokół |Protokół, który jest stosowany przez warstwę transportu dla tego punktu końcowego, TCP lub UDP. |
   | Port publiczny |Port używany do publicznego dostępu do aplikacji. |
