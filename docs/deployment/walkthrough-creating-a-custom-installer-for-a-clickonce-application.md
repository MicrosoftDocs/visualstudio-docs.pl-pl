---
title: Tworzenie niestandardowego Instalatora dla aplikacji ClickOnce
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, custom installer
- installer [ClickOnce], custom
- deploying applications [ClickOnce], custom installer
- InPlaceHostingManager [ClickOnce], custom installer
- custom installer [ClickOnce]
ms.assetid: fb222cc5-8aeb-4b94-8c49-b93e342f5f69
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: b648134b7ad27a8f622ce270dc0f05e0a7e6516c
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/19/2019
ms.locfileid: "72637422"
---
# <a name="walkthrough-create-a-custom-installer-for-a-clickonce-application"></a>Przewodnik: Tworzenie niestandardowego Instalatora dla aplikacji ClickOnce
Wszystkie aplikacje ClickOnce oparte na pliku *. exe* mogą być instalowane w trybie dyskretnym i aktualizowane przez instalatora niestandardowego. Instalator niestandardowy może zaimplementować niestandardowe środowisko użytkownika podczas instalacji, w tym niestandardowe okna dialogowe dla operacji związanych z zabezpieczeniami i konserwacją. W celu wykonania operacji instalacji Instalator niestandardowy używa klasy <xref:System.Deployment.Application.InPlaceHostingManager>. W tym instruktażu przedstawiono sposób tworzenia niestandardowego Instalatora, który dyskretnie instaluje aplikację ClickOnce.

## <a name="prerequisites"></a>Wymagania wstępne

### <a name="to-create-a-custom-clickonce-application-installer"></a>Aby utworzyć niestandardowy Instalator aplikacji ClickOnce

1. W aplikacji ClickOnce Dodaj odwołania do System. Deployment i system. Windows. Forms.

2. Dodaj nową klasę do aplikacji i określ dowolną nazwę. W tym instruktażu zostanie użyta nazwa `MyInstaller`.

3. Dodaj następujące dyrektywy `Imports` lub `using` na początku nowej klasy.

    ```vb
    Imports System.Deployment.Application
    Imports System.Windows.Forms
    ```

    ```csharp
    using System.Deployment.Application;
    using System.Windows.Forms;
    ```

4. Dodaj następujące metody do klasy.

     Te metody wywołują <xref:System.Deployment.Application.InPlaceHostingManager> metod pobrania manifestu wdrożenia, potwierdzenia odpowiednich uprawnień, poproszenia użytkownika o zgodę na instalację, a następnie pobranie i zainstalowanie aplikacji w pamięci podręcznej ClickOnce. Instalator niestandardowy może określić, że aplikacja ClickOnce jest wstępnie zaufana, lub może odroczyć decyzję zaufania do wywołania metody <xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A>. Ten kod wstępnie ufa aplikacji.

    > [!NOTE]
    > Uprawnienia przypisane przez przed zaufaniem nie mogą przekroczyć uprawnień do niestandardowego kodu Instalatora.

     [!code-vb[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/VisualBasic/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.vb)]
     [!code-csharp[System.Deployment.Application.InPlaceHostingManager#1](../deployment/codesnippet/CSharp/walkthrough-creating-a-custom-installer-for-a-clickonce-application_1.cs)]

5. Aby podjąć próbę instalacji z kodu, wywołaj metodę `InstallApplication`. Na przykład, jeśli nazwa klasy `MyInstaller`, możesz wywołać `InstallApplication` w następujący sposób.

    ```vb
    Dim installer As New MyInstaller()
    installer.InstallApplication("\\myServer\myShare\myApp.application")
    MessageBox.Show("Installer object created.")
    ```

    ```csharp
    MyInstaller installer = new MyInstaller();
    installer.InstallApplication(@"\\myServer\myShare\myApp.application");
    MessageBox.Show("Installer object created.");
    ```

## <a name="next-steps"></a>Następne kroki
 Aplikacja ClickOnce może również dodać niestandardową logikę aktualizacji, w tym niestandardowy interfejs użytkownika do wyświetlania w trakcie procesu aktualizacji. Aby uzyskać więcej informacji, zobacz <xref:System.Deployment.Application.UpdateCheckInfo>. Aplikacja ClickOnce może również pominąć standardowe pozycje menu Start, skrót i Dodaj lub usuń programy za pomocą elementu `<customUX>`. Aby uzyskać więcej informacji, zobacz [\<entryPoint > elementu](../deployment/entrypoint-element-clickonce-application.md) i <xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A>.

## <a name="see-also"></a>Zobacz także
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)
- [Element > \<entryPoint](../deployment/entrypoint-element-clickonce-application.md)
