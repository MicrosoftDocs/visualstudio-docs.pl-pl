---
title: Automatyczne aktualizacje aplikacji korzystające z interfejsu API wdrażania technologii ClickOnce
description: Dowiedz się, jak napisać kod w technologii ClickOnce, która używa klasy ApplicationDeployment w celu sprawdzenia dostępności aktualizacji na podstawie zdarzenia, takiego jak żądanie użytkownika.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, updates
- application updates
ms.assetid: 1a886310-67c8-44e5-a382-c2f0454f887d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f00bd8aaa5db8ab72e6b6286763fd89fc900599f
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94351261"
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>Jak: sprawdzanie aktualizacji aplikacji programowo przy użyciu interfejsu API wdrażania ClickOnce
Technologia ClickOnce oferuje dwa sposoby aktualizowania aplikacji po jej wdrożeniu. W pierwszej metodzie można skonfigurować wdrożenie ClickOnce, aby automatycznie sprawdzać dostępność aktualizacji w określonych odstępach czasu. W drugiej metodzie można napisać kod, który używa <xref:System.Deployment.Application.ApplicationDeployment> klasy do sprawdzania dostępności aktualizacji na podstawie zdarzenia, takiego jak żądanie użytkownika.

 W poniższych procedurach przedstawiono kod służący do przeprowadzania aktualizacji programowych, a także opisano sposób konfigurowania wdrożenia technologii ClickOnce w celu włączenia kontroli aktualizacji programistycznych.

 Aby programowo zaktualizować aplikację ClickOnce, należy określić lokalizację dla aktualizacji. Jest to czasami określane jako dostawca wdrożenia. Aby uzyskać więcej informacji na temat ustawiania tej właściwości, zobacz [Wybieranie strategii aktualizacji ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).

> [!NOTE]
> Możesz również użyć opisanej poniżej techniki, aby wdrożyć aplikację z jednej lokalizacji, ale zaktualizować ją z innej. Aby uzyskać więcej informacji, zobacz [How to: Określanie alternatywnej lokalizacji aktualizacji wdrożenia](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md).

### <a name="to-check-for-updates-programmatically"></a>Aby programowo sprawdzić dostępność aktualizacji

1. Utwórz nową aplikację Windows Forms przy użyciu preferowanych narzędzi wiersza polecenia lub wizualizacji.

2. Utwórz dowolny przycisk, element menu lub inny element interfejsu użytkownika, który chcesz, aby użytkownicy wybierali aktualizacje. Z procedury obsługi zdarzeń tego elementu Wywołaj następującą metodę, aby sprawdzić i zainstalować aktualizacje.

     [!code-csharp[ClickOnceAPI#6](../deployment/codesnippet/CSharp/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cs)]
     [!code-cpp[ClickOnceAPI#6](../deployment/codesnippet/CPP/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cpp)]
     [!code-vb[ClickOnceAPI#6](../deployment/codesnippet/VisualBasic/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.vb)]

3. Kompiluj aplikację.

### <a name="use-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Użyj Mage.exe, aby wdrożyć aplikację, która programowo sprawdza dostępność aktualizacji

- Postępuj zgodnie z instrukcjami dotyczącymi wdrażania aplikacji przy użyciu Mage.exe, jak wyjaśniono w [przewodniku: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Podczas wywoływania Mage.exe w celu wygenerowania manifestu wdrażania upewnij się, że używasz przełącznika wiersza polecenia `providerUrl` i określ adres URL, pod którym ClickOnce powinna sprawdzać dostępność aktualizacji. Jeśli aplikacja zostanie zaktualizowana `http://www.adatum.com/MyApp` , na przykład, wywołanie wygenerowania manifestu wdrożenia może wyglądać następująco:

    ```cmd
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application
    ```

### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Używanie MageUI.exe do wdrożenia aplikacji, która programowo sprawdza dostępność aktualizacji

- Postępuj zgodnie z instrukcjami dotyczącymi wdrażania aplikacji przy użyciu Mage.exe, jak wyjaśniono w [przewodniku: ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Na karcie **Opcje wdrażania** Ustaw pole **Lokalizacja początkowa** na manifest aplikacji ClickOnce powinna sprawdzać dostępność aktualizacji. Na karcie **Opcje aktualizacji** wyczyść pole wyboru **Ta aplikacja powinna sprawdzać dostępność aktualizacji** .

## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework
 Aby można było korzystać z aktualizacji programistycznych, aplikacja musi mieć uprawnienia pełnego zaufania.

## <a name="see-also"></a>Zobacz też
- [Instrukcje: Określanie alternatywnej lokalizacji aktualizacji wdrożenia](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)
- [Wybieranie strategii aktualizacji ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
- [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)