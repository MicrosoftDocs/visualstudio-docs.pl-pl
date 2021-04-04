---
title: Tworzenie niestandardowego Instalatora dla aplikacji ClickOnce
description: Dowiedz się, w jaki sposób Instalator niestandardowy może dyskretnie zainstalować i zaktualizować aplikację ClickOnce na podstawie pliku. exe.
ms.custom: SEO-VS-2020
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
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: e7ae131026a94fa368d55bad1d8cd2164b6f960b
ms.sourcegitcommit: 80fc9a72e9a1aba2d417dbfee997fab013fc36ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/02/2021
ms.locfileid: "106216933"
---
# <a name="walkthrough-create-a-custom-installer-for-a-clickonce-application"></a>Przewodnik: Tworzenie niestandardowego Instalatora dla aplikacji ClickOnce
Wszystkie aplikacje ClickOnce oparte na pliku *. exe* mogą być instalowane w trybie dyskretnym i aktualizowane przez instalatora niestandardowego. Instalator niestandardowy może zaimplementować niestandardowe środowisko użytkownika podczas instalacji, w tym niestandardowe okna dialogowe dla operacji związanych z zabezpieczeniami i konserwacją. W celu wykonania operacji instalacji Instalator niestandardowy używa <xref:System.Deployment.Application.InPlaceHostingManager> klasy. W tym instruktażu przedstawiono sposób tworzenia niestandardowego Instalatora, który dyskretnie instaluje aplikację ClickOnce.

## <a name="prerequisites"></a>Wymagania wstępne

### <a name="to-create-a-custom-clickonce-application-installer"></a>Aby utworzyć niestandardowy Instalator aplikacji ClickOnce

1. W aplikacji ClickOnce Dodaj odwołania do System. Deployment i system. Windows. Forms.

2. Dodaj nową klasę do aplikacji i określ dowolną nazwę. W tym instruktażu zostanie użyta nazwa `MyInstaller` .

3. Dodaj poniższe `Imports` lub `using` dyrektywy na początku nowej klasy.

    ```vb
    Imports System.Deployment.Application
    Imports System.Windows.Forms
    ```

    ```csharp
    using System.Deployment.Application;
    using System.Windows.Forms;
    ```

4. Dodaj następujące metody do klasy.

     Metody te wywołują <xref:System.Deployment.Application.InPlaceHostingManager> metody pobierania manifestu wdrożenia, potwierdzenia odpowiednich uprawnień, poproszenia użytkownika o zgodę na instalację, a następnie pobranie i zainstalowanie aplikacji w pamięci podręcznej ClickOnce. Instalator niestandardowy może określić, że aplikacja ClickOnce jest wstępnie zaufana, lub może odroczyć decyzję zaufania do <xref:System.Deployment.Application.InPlaceHostingManager.AssertApplicationRequirements%2A> wywołania metody. Ten kod wstępnie ufa aplikacji.

    > [!NOTE]
    > Uprawnienia przypisane przez przed zaufaniem nie mogą przekroczyć uprawnień do niestandardowego kodu Instalatora.

    :::code language="vb" source="../snippets/visualbasic/VS_Snippets_Winforms/System.Deployment.Application.InPlaceHostingManager/VB/Form1.vb" id="Snippet1":::
    :::code language="csharp" source="../snippets/csharp/VS_Snippets_Winforms/System.Deployment.Application.InPlaceHostingManager/CS/Form1.cs" id="Snippet1":::

5. Aby podjąć próbę instalacji z kodu, wywołaj `InstallApplication` metodę. Na przykład, jeśli nazwa klasy istnieje `MyInstaller` , można wywołać `InstallApplication` w następujący sposób.

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
 Aplikacja ClickOnce może również dodać niestandardową logikę aktualizacji, w tym niestandardowy interfejs użytkownika do wyświetlania w trakcie procesu aktualizacji. Aby uzyskać więcej informacji, zobacz <xref:System.Deployment.Application.UpdateCheckInfo>. Aplikacja ClickOnce może również pominąć standardowy wpis menu Start, skrót i Dodaj lub usuń programy za pomocą `<customUX>` elementu. Aby uzyskać więcej informacji, zobacz [ \<entryPoint> element](../deployment/entrypoint-element-clickonce-application.md) i <xref:System.Deployment.Application.DownloadApplicationCompletedEventArgs.ShortcutAppId%2A> .

## <a name="see-also"></a>Zobacz też
- [Manifest aplikacji ClickOnce](../deployment/clickonce-application-manifest.md)
- [\<entryPoint> postaci](../deployment/entrypoint-element-clickonce-application.md)
