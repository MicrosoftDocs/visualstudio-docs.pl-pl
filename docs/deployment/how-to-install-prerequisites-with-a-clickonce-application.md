---
title: Instalowanie wymagań wstępnych przy użyciu aplikacji ClickOnce
description: Dowiedz się, jak wybrać wstępnie wymagane składniki do spakowania wraz z aplikacją ClickOnce podczas instalacji.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- deploying applications [ClickOnce], prerequisites
- prerequisites, ClickOnce
- components, bootstrapping
ms.assetid: e964fca5-fdfd-47cf-a1c9-7fb96b1c88b5
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 09337ee164c8b740e9aa8a044c4a9df385f01016
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900570"
---
# <a name="how-to-install-prerequisites-with-a-clickonce-application"></a>Instrukcje: instalowanie wstępnie wymaganych składników za pomocą aplikacji ClickOnce
Wszystkie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje wymagają, aby poprawna wersja .NET Framework była zainstalowana na komputerze, zanim będzie można go uruchomić. wiele aplikacji również ma inne wymagania wstępne. Podczas publikowania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji można wybrać zestaw wstępnie wymaganych składników do spakowania wraz z aplikacją. Podczas instalacji dla każdego wymagania wstępnego zostanie wykonane sprawdzenie w celu ustalenia, czy już istnieje; w przeciwnym razie zostanie zainstalowana przed zainstalowaniem [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji.

 Zamiast pakowania i publikowania wymagań wstępnych można także określić lokalizację pobierania dla składników. Na przykład zamiast uwzględniać wymagania wstępne dla każdej opublikowanej aplikacji, można użyć scentralizowanego udziału plików lub lokalizacji sieci Web, która zawiera Instalatory dla wszystkich wymagań wstępnych — w czasie instalacji składniki zostaną pobrane i zainstalowane z tej lokalizacji.

> [!IMPORTANT]
> Przed opublikowaniem pierwszej aplikacji należy dodać wstępnie wymagane pakiety Instalatora do komputera deweloperskiego [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] . Aby uzyskać więcej informacji, zobacz [How to: dołączanie wymagań wstępnych do aplikacji ClickOnce](../deployment/how-to-include-prerequisites-with-a-clickonce-application.md).

 Wymagania wstępne są zarządzane w oknie dialogowym **wymagania wstępne** dostępne z okienka **Publikowanie** **projektanta projektu**.

> [!NOTE]
> Oprócz wstępnie określonej listy wymagań wstępnych można dodać własne składniki do listy. Aby uzyskać więcej informacji, zobacz [Tworzenie pakietów programu inicjującego](../deployment/creating-bootstrapper-packages.md).

### <a name="to-specify-prerequisites-to-install-with-a-clickonce-application"></a>Aby określić wymagania wstępne instalacji przy użyciu aplikacji ClickOnce

1. Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.

2. Wybierz okienko **Publikowanie** .

3. Kliknij przycisk **wymagania wstępne** , aby otworzyć okno dialogowe **wymagania wstępne** .

4. W oknie dialogowym **wymagania wstępne** upewnij się, że jest zaznaczone pole wyboru **Utwórz program instalacyjny, aby zainstalować wstępnie wymagane składniki** .

5. Na liście **wymagania wstępne** zaznacz składniki, które chcesz zainstalować, a następnie kliknij przycisk **OK**.

     Wybrane składniki zostaną spakowane i opublikowane razem z aplikacją.

### <a name="to-specify-a-different-download-location-for-prerequisites"></a>Aby określić inną lokalizację pobierania dla wymagań wstępnych

1. Po wybraniu projektu w **Eksplorator rozwiązań**, w menu **projekt** kliknij polecenie **Właściwości**.

2. Wybierz okienko **Publikowanie** .

3. Kliknij przycisk **wymagania wstępne** , aby otworzyć okno dialogowe **wymagania wstępne** .

4. W oknie dialogowym **wymagania wstępne** upewnij się, że jest zaznaczone pole wyboru **Utwórz program instalacyjny, aby zainstalować wstępnie wymagane składniki** .

5. W sekcji **Określ lokalizację instalacji dla wymagań wstępnych** wybierz pozycję **Pobierz wymagania wstępne z następującej lokalizacji**.

6. Wybierz lokalizację z listy rozwijanej lub wprowadź adres URL, ścieżkę pliku lub lokalizację FTP, a następnie kliknij przycisk **OK.**

    > [!NOTE]
    > Należy upewnić się, że Instalatory dla określonych składników istnieją w określonej lokalizacji.

## <a name="see-also"></a>Zobacz też
- [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Instrukcje: publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)