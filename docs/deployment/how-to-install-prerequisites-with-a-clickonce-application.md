---
title: 'Instrukcje: Instalowanie wymagań wstępnych przy użyciu aplikacji ClickOnce | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 047ac897931cbb93d8a06406e300d39cd83a9fe4
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63406749"
---
# <a name="how-to-install-prerequisites-with-a-clickonce-application"></a>Instrukcje: Instalowanie wymagań wstępnych przy użyciu aplikacji ClickOnce
Wszystkie [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacje wymagają poprawną wersję programu .NET Framework jest zainstalowanie na komputerze przed zadania mogą być uruchamiane; wiele aplikacji ma również inne wymagania wstępne. Podczas publikowania [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji, można wybrać zestaw wstępnie wymagane składniki do umieszczenia w pakiecie wraz z aplikacji. W trakcie instalacji będą sprawdzane dla poszczególnych wymagań wstępnych określić, jeśli już istnieje; Jeśli nie zostanie zainstalowany przed zainstalowaniem [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji.

 Zamiast pakowanie i publikowania wymagań wstępnych, można również określić lokalizację pobierania dla składników. Na przykład, zamiast w tym wstępnie wymaganych składników w każdej publikowanej aplikacji, można na przykład udział scentralizowanego pliku lub lokalizacji w sieci Web, który zawiera pliki instalacyjne, wszystkie Twoje wymagania wstępne — w czasie instalacji składników zostaną pobrane i instalowane z tej lokalizacji.

> [!IMPORTANT]
> Należy dodać pakietów wymagań wstępnych Instalatora na komputerze dewelopera, przed opublikowaniem pierwszej [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji. Aby uzyskać więcej informacji, zobacz [jak: Uwzględnianie wstępnie wymaganych składników w aplikacji ClickOnce](../deployment/how-to-include-prerequisites-with-a-clickonce-application.md).

 Wymagania wstępne są zarządzane w **wymagania wstępne** okno dialogowe, dostępna z **Publikuj** okienku **projektanta projektu**.

> [!NOTE]
> Oprócz listy wstępnie zdefiniowanych wymagań wstępnych można dodać własne składniki do listy. Aby uzyskać więcej informacji, zobacz [tworzenie pakietów programu inicjującego](../deployment/creating-bootstrapper-packages.md).

### <a name="to-specify-prerequisites-to-install-with-a-clickonce-application"></a>Aby określić wymagania wstępne dotyczące instalacji za pomocą aplikacji ClickOnce

1. Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** kliknij menu **właściwości**.

2. Wybierz **Publikuj** okienka.

3. Kliknij przycisk **wymagania wstępne** przycisk, aby otworzyć **wymagania wstępne** okno dialogowe.

4. W **wymagania wstępne** okna dialogowego pole, upewnij się, że **Utwórz program instalacyjny, aby zainstalować wstępnie wymagane składniki** pole wyboru jest zaznaczone.

5. W **wymagania wstępne** listy, należy sprawdzić te składniki, które chcesz zainstalować, a następnie kliknij przycisk **OK**.

     Wybrane składniki zostaną spakowane i opublikowanych wraz z aplikacji.

### <a name="to-specify-a-different-download-location-for-prerequisites"></a>Aby określić lokalizację pobierania różnych wstępnie wymaganych składników

1. Za pomocą projektu wybranego w **Eksploratora rozwiązań**na **projektu** kliknij menu **właściwości**.

2. Wybierz **Publikuj** okienka.

3. Kliknij przycisk **wymagania wstępne** przycisk, aby otworzyć **wymagania wstępne** okno dialogowe.

4. W **wymagania wstępne** okna dialogowego pole, upewnij się, że **Utwórz program instalacyjny, aby zainstalować wstępnie wymagane składniki** pole wyboru jest zaznaczone.

5. W **Określ lokalizację instalacji wstępnie wymaganych składników** zaznacz **Pobierz wstępnie wymagane składniki z następującej lokalizacji**.

6. Wybierz lokalizację z listy rozwijanej lub wprowadź adres URL, ścieżkę pliku lub lokalizację FTP, a następnie kliknij **OK.**

    > [!NOTE]
    > Upewnij się, że instalatory dla określone składniki istnieje w określonej lokalizacji.

## <a name="see-also"></a>Zobacz także
- [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)
- [Instrukcje: Publikowanie aplikacji ClickOnce za pomocą Kreatora publikacji](../deployment/how-to-publish-a-clickonce-application-using-the-publish-wizard.md)