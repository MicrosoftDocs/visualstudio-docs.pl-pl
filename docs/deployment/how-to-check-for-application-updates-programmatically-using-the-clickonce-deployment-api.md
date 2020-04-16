---
title: Automatyczne aktualizacje aplikacji przy użyciu interfejsu API wdrażania ClickOnce
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: 9300fbf8b348b1016d36d414d17a66c45f6494b9
ms.sourcegitcommit: 7b60e81414a82c6d34f6de1a1f56115c9cd26943
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81444620"
---
# <a name="how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api"></a>Jak: Sprawdzanie aktualizacji aplikacji programowo przy użyciu interfejsu API wdrażania ClickOnce
ClickOnce udostępnia dwa sposoby, aby zaktualizować aplikację po jej wdrożeniu. W pierwszej metodzie można skonfigurować ClickOnce wdrożenia, aby automatycznie sprawdzać aktualizacje w określonych odstępach czasu. W drugiej metodzie można napisać kod, <xref:System.Deployment.Application.ApplicationDeployment> który używa klasy, aby sprawdzić aktualizacje na podstawie zdarzenia, takich jak żądanie użytkownika.

 Poniższe procedury pokazują kod do wykonywania aktualizacji programowej, a także opisano, jak skonfigurować wdrożenie ClickOnce, aby włączyć sprawdzanie aktualizacji programowej.

 Aby programowo zaktualizować aplikację ClickOnce, należy określić lokalizację aktualizacji. Jest to czasami określane jako dostawca wdrażania. Aby uzyskać więcej informacji na temat ustawiania tej właściwości, zobacz [Wybieranie strategii aktualizacji ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md).

> [!NOTE]
> Można również użyć techniki opisanej poniżej, aby wdrożyć aplikację z jednej lokalizacji, ale zaktualizować ją z innej. Aby uzyskać więcej informacji, zobacz [Jak: Określanie alternatywnej lokalizacji aktualizacji wdrażania](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md).

### <a name="to-check-for-updates-programmatically"></a>Aby sprawdzić dostępność aktualizacji programowo

1. Utwórz nową aplikację Windows Forms przy użyciu preferowanych narzędzi wiersza polecenia lub narzędzi wizualnych.

2. Utwórz dowolny przycisk, element menu lub inny element interfejsu użytkownika, który chcesz wybrać użytkowników, aby sprawdzić dostępność aktualizacji. Z obsługi zdarzeń tego elementu, wywołać następującą metodę, aby sprawdzić i zainstalować aktualizacje.

     [!code-csharp[ClickOnceAPI#6](../deployment/codesnippet/CSharp/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cs)]
     [!code-cpp[ClickOnceAPI#6](../deployment/codesnippet/CPP/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.cpp)]
     [!code-vb[ClickOnceAPI#6](../deployment/codesnippet/VisualBasic/how-to-check-for-application-updates-programmatically-using-the-clickonce-deployment-api_1.vb)]

3. Skompiluj aplikację.

### <a name="use-mageexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Program Mage.exe umożliwia wdrożenie aplikacji, która programowo sprawdza dostępność aktualizacji

- Postępuj zgodnie z instrukcjami dotyczącymi wdrażania aplikacji przy użyciu programu Mage.exe, jak wyjaśniono w [przewodniku: Ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Podczas wywoływania programu Mage.exe w celu wygenerowania manifestu `providerUrl`wdrożenia należy użyć przełącznika wiersza polecenia i określić adres URL, pod którym ClickOnce powinien sprawdzić dostępność aktualizacji. Jeśli aplikacja zostanie `http://www.adatum.com/MyApp`zaktualizowana z , na przykład wywołanie generowania manifestu wdrożenia może wyglądać następująco:

    ```cmd
    mage -New Deployment -ToFile WindowsFormsApp1.application -Name "My App 1.0" -Version 1.0.0.0 -AppManifest 1.0.0.0\MyApp.manifest -providerUrl http://www.adatum.com/MyApp/MyApp.application
    ```

### <a name="using-mageuiexe-to-deploy-an-application-that-checks-for-updates-programmatically"></a>Używanie programu MageUI.exe do wdrażania aplikacji, która sprawdza dostępność aktualizacji programowo

- Postępuj zgodnie z instrukcjami dotyczącymi wdrażania aplikacji przy użyciu programu Mage.exe, jak wyjaśniono w [przewodniku: Ręczne wdrażanie aplikacji ClickOnce](../deployment/walkthrough-manually-deploying-a-clickonce-application.md). Na karcie **Opcje wdrażania** ustaw pole **Rozpocznij lokalizację** na manifest aplikacji ClickOnce powinien sprawdzić dostępność aktualizacji. Na karcie **Opcje aktualizacji** wyczyść pole wyboru Ta aplikacja powinna sprawdzić **dostępność aktualizacji.**

## <a name="net-framework-security"></a>Zabezpieczenia.NET Framework
 Aplikacja musi mieć uprawnienia pełnego zaufania do korzystania z aktualizacji programowej.

## <a name="see-also"></a>Zobacz też
- [Jak: Określanie alternatywnej lokalizacji aktualizacji wdrażania](../deployment/how-to-specify-an-alternate-location-for-deployment-updates.md)
- [Wybieranie strategii aktualizacji ClickOnce](../deployment/choosing-a-clickonce-update-strategy.md)
- [Publikowanie aplikacji ClickOnce](../deployment/publishing-clickonce-applications.md)