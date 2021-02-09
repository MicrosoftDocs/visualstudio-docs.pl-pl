---
title: Ponowne podpisywanie aplikacji i manifestów wdrożenia | Microsoft Docs
description: Informacje o ponownym podpisywaniu aplikacji i manifestów wdrożenia za pomocą certyfikatu po wprowadzeniu zmian w właściwościach wdrożenia.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- Office applications, signing manifests
- deploying applications [ClickOnce], signing manifests
- deploying applications, signing manifests
- ClickOnce deployment, signing manifests
- Office development in Visual Studio, signing manifests
ms.assetid: d53bceb9-4d3b-4c22-b909-8f370e7231fb
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 0b4e4efee02ca1571f40ae33f9d69d8fbec0a1d1
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900437"
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>Instrukcje: ponowne podpisywanie aplikacji i manifestów wdrożenia
Po wprowadzeniu zmian we właściwościach wdrożenia w manifeście aplikacji dla aplikacji Windows Forms, aplikacji Windows Presentation Foundation (XBAP) lub rozwiązań pakietu Office należy jeszcze raz podpisać aplikacje i manifesty wdrożenia przy użyciu certyfikatu. Ten proces zapewnia, że naruszone pliki nie są zainstalowane na komputerach użytkowników końcowych.

 Innym scenariuszem, w którym można podpisywać manifesty, jest to, że klienci chcą podpisać aplikacje i manifesty wdrożenia przy użyciu własnego certyfikatu.

## <a name="re-sign-the-application-and-deployment-manifests"></a>Ponowne podpisywanie aplikacji i manifestów wdrożenia
 W tej procedurze przyjęto założenie, że wprowadzono już zmiany w pliku manifestu aplikacji (*manifest*). Aby uzyskać więcej informacji, zobacz [How to: Change Deployment Properties](/previous-versions/cc442869(v=vs.110)).

#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Aby ponowne podpisać aplikacje i manifesty wdrożenia za pomocą Mage.exe

1. Otwórz okno **wiersza polecenia programu Visual Studio** .

2. Zmień katalogi na folder zawierający pliki manifestu, które chcesz podpisać.

3. Wpisz następujące polecenie, aby podpisać plik manifestu aplikacji. Zastąp *ManifestFileName* nazwą pliku manifestu oraz rozszerzeniem. Zastąp *certyfikat* ścieżką względną lub w pełni kwalifikowaną nazwą pliku certyfikatu i Zastąp *hasło* hasłem dla certyfikatu.

    ```cmd
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password
    ```

     Na przykład można uruchomić następujące polecenie, aby podpisać manifest aplikacji dla dodatku, aplikacji formularzy systemu Windows lub aplikacji w Windows Presentation Foundation Browser. Nie zaleca się wdrażania certyfikatów tymczasowych utworzonych przez program Visual Studio w środowiskach produkcyjnych.

    ```cmd
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

4. Wpisz następujące polecenie, aby zaktualizować i podpisać plik manifestu wdrożenia, zastępując nazwy symboli zastępczych jak w poprzednim kroku.

    ```cmd
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password
    ```

     Można na przykład uruchomić następujące polecenie, aby zaktualizować i podpisać manifest wdrożenia dla dodatku programu Excel, aplikacji Windows Forms lub aplikacji przeglądarki Windows Presentation Foundation.

    ```cmd
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

5. Opcjonalnie Skopiuj manifest wdrożenia głównego (*Publish \\ \<appname> . Application*) do katalogu wdrożenia wersji (*pliki publish\Application \\ \<appname> _ \<version>*).

## <a name="update-and-re-sign-the-application-and-deployment-manifests"></a>Aktualizowanie i ponowne podpisywanie aplikacji i manifestów wdrożenia
 W tej procedurze przyjęto założenie, że wprowadzono już zmiany w pliku manifestu aplikacji (*manifest*), ale istnieją inne pliki, które zostały zaktualizowane. Gdy pliki są aktualizowane, skrót reprezentujący plik musi również zostać zaktualizowany.

#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Aby zaktualizować i podpisać aplikacje i manifesty wdrożenia za pomocą Mage.exe

1. Otwórz okno **wiersza polecenia programu Visual Studio** .

2. Zmień katalogi na folder zawierający pliki manifestu, które chcesz podpisać.

3. Usuń rozszerzenie *. deploy* pliku z plików w folderze danych wyjściowych publikowania.

4. Wpisz następujące polecenie, aby zaktualizować manifest aplikacji przy użyciu nowych skrótów dla zaktualizowanych plików, a następnie podpisz plik manifestu aplikacji. Zastąp *ManifestFileName* nazwą pliku manifestu oraz rozszerzeniem. Zastąp *certyfikat* ścieżką względną lub w pełni kwalifikowaną nazwą pliku certyfikatu i Zastąp *hasło* hasłem dla certyfikatu.

    ```cmd
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password
    ```

     Na przykład można uruchomić następujące polecenie, aby podpisać manifest aplikacji dla dodatku, aplikacji formularzy systemu Windows lub aplikacji w Windows Presentation Foundation Browser. Nie zaleca się wdrażania certyfikatów tymczasowych utworzonych przez program Visual Studio w środowiskach produkcyjnych.

    ```cmd
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

5. Wpisz następujące polecenie, aby zaktualizować i podpisać plik manifestu wdrożenia, zastępując nazwy symboli zastępczych jak w poprzednim kroku.

    ```cmd
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password
    ```

     Można na przykład uruchomić następujące polecenie, aby zaktualizować i podpisać manifest wdrożenia dla dodatku programu Excel, aplikacji Windows Forms lub aplikacji przeglądarki Windows Presentation Foundation.

    ```cmd
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

6. Dodaj rozszerzenie *. deploy* z powrotem do plików, z wyjątkiem plików manifestu aplikacji i wdrożenia.

7. Opcjonalnie Skopiuj manifest wdrożenia głównego (*Publish \\ \<appname> . Application*) do katalogu wdrożenia wersji (*pliki publish\Application \\ \<appname> _ \<version>*).

## <a name="see-also"></a>Zobacz też
- [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)
- [Zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
- [ClickOnce i podpis Authenticode](../deployment/clickonce-and-authenticode.md)
- [Omówienie wdrażania zaufanych aplikacji](../deployment/trusted-application-deployment-overview.md)
- [Instrukcje: Włączanie ustawień zabezpieczeń technologii ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)
- [Instrukcje: Ustawianie strefy zabezpieczeń dla aplikacji ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Instrukcje: Ustawianie uprawnień niestandardowych dla aplikacji ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Instrukcje: debugowanie aplikacji ClickOnce z ograniczonymi uprawnieniami](securing-clickonce-applications.md)
- [Instrukcje: Dodawanie zaufanego wydawcy do komputera klienckiego dla aplikacji ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [Instrukcje: Konfigurowanie zachowania monitowania zaufania ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)