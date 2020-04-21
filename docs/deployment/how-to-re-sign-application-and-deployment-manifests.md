---
title: 'Jak: Ponowne podpisywanie manifestów aplikacji i wdrażania | Dokumenty firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
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
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: fc69ce1f79644d7f4b35fbb1c1e3a41691761390
ms.sourcegitcommit: ade07bd1cf69b8b494d171ae648cfdd54f7800d3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/21/2020
ms.locfileid: "81649186"
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>Jak: Ponowne podpisywanie manifestów aplikacji i wdrażania
Po wdrożeniu zmian właściwości wdrażania w manifeście aplikacji dla aplikacji Windows Forms, Windows Presentation Foundation (xbap) lub rozwiązania pakietu Office należy ponownie podpisać manifesty aplikacji i wdrożenia za pomocą certyfikatu. Ten proces pomaga zapewnić, że zmodyfikowane pliki nie są zainstalowane na komputerach użytkowników końcowych.

 Innym scenariuszem, w którym można ponownie podpisać manifesty jest, gdy klienci chcą podpisać manifesty aplikacji i wdrażania z własnym certyfikatem.

## <a name="re-sign-the-application-and-deployment-manifests"></a>Ponowne podpisywanie manifestów aplikacji i wdrażania
 W tej procedurze przyjęto założenie, że w pliku manifestu aplikacji wprowadzono już zmiany (*manifest*). Aby uzyskać więcej informacji, zobacz [Jak: Zmienianie właściwości wdrażania](https://msdn.microsoft.com/library/66052a3a-8127-4964-8147-2477ef5d1472).

#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Aby ponownie podpisać manifesty aplikacji i wdrażania za pomocą programu Mage.exe

1. Otwórz okno **wiersza polecenia programu Visual Studio.**

2. Zmień katalogi na folder zawierający pliki manifestu, które chcesz podpisać.

3. Wpisz następujące polecenie, aby podpisać plik manifestu aplikacji. Zastąp *ManifestFileName* nazwą pliku manifestu oraz rozszerzeniem. Zastąp *certyfikat* względną lub w pełni kwalifikowaną ścieżką pliku certyfikatu i zastąp *hasło* hasłem certyfikatu.

    ```cmd
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password
    ```

     Na przykład można uruchomić następujące polecenie, aby podpisać manifest aplikacji dla dodatku, aplikacji formularza systemu Windows lub aplikacji przeglądarki Windows Presentation Foundation. Tymczasowe certyfikaty utworzone przez program Visual Studio nie są zalecane do wdrożenia w środowiskach produkcyjnych.

    ```cmd
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

4. Wpisz następujące polecenie, aby zaktualizować i podpisać plik manifestu wdrożenia, zastępując nazwy symboli zastępczych, jak w poprzednim kroku.

    ```cmd
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password
    ```

     Na przykład można uruchomić następujące polecenie, aby zaktualizować i podpisać manifest wdrożenia dla dodatku programu Excel, aplikacji Windows Forms lub aplikacji przeglądarki Windows Presentation Foundation.

    ```cmd
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

5. Opcjonalnie skopiuj manifest wdrożenia głównego*\\\<(publikuj appname>.application)* do katalogu wdrażania wersji (*publikuj\Pliki aplikacji\\\<\<appname>_ wersja>*).

## <a name="update-and-re-sign-the-application-and-deployment-manifests"></a>Aktualizowanie i ponowne podpisywanie manifestów aplikacji i wdrażania
 W tej procedurze założono, że wprowadzono już zmiany w pliku manifestu aplikacji (*manifest*), ale istnieją inne pliki, które zostały zaktualizowane. Po zaktualizowaniu plików skrót reprezentujący plik również musi zostać zaktualizowany.

#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Aby zaktualizować i ponownie podpisać manifesty aplikacji i wdrażania za pomocą programu Mage.exe

1. Otwórz okno **wiersza polecenia programu Visual Studio.**

2. Zmień katalogi na folder zawierający pliki manifestu, które chcesz podpisać.

3. Usuń rozszerzenie pliku *.deploy* z plików w folderze wyjścia publikowania.

4. Wpisz następujące polecenie, aby zaktualizować manifest aplikacji za pomocą nowych skrótów zaktualizowanych plików i podpisać plik manifestu aplikacji. Zastąp *ManifestFileName* nazwą pliku manifestu oraz rozszerzeniem. Zastąp *certyfikat* względną lub w pełni kwalifikowaną ścieżką pliku certyfikatu i zastąp *hasło* hasłem certyfikatu.

    ```cmd
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password
    ```

     Na przykład można uruchomić następujące polecenie, aby podpisać manifest aplikacji dla dodatku, aplikacji formularza systemu Windows lub aplikacji przeglądarki Windows Presentation Foundation. Tymczasowe certyfikaty utworzone przez program Visual Studio nie są zalecane do wdrożenia w środowiskach produkcyjnych.

    ```cmd
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

5. Wpisz następujące polecenie, aby zaktualizować i podpisać plik manifestu wdrożenia, zastępując nazwy symboli zastępczych, jak w poprzednim kroku.

    ```cmd
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password
    ```

     Na przykład można uruchomić następujące polecenie, aby zaktualizować i podpisać manifest wdrożenia dla dodatku programu Excel, aplikacji Windows Forms lub aplikacji przeglądarki Windows Presentation Foundation.

    ```cmd
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx
    ```

6. Dodaj rozszerzenie pliku *.deploy* z powrotem do plików, z wyjątkiem plików manifestu aplikacji i wdrożenia.

7. Opcjonalnie skopiuj manifest wdrożenia głównego*\\\<(publikuj appname>.application)* do katalogu wdrażania wersji (*publikuj\Pliki aplikacji\\\<\<appname>_ wersja>*).

## <a name="see-also"></a>Zobacz też
- [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)
- [Zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
- [ClickOnce i podpis Authenticode](../deployment/clickonce-and-authenticode.md)
- [Omówienie wdrażania zaufanych aplikacji](../deployment/trusted-application-deployment-overview.md)
- [Jak: Włącz ustawienia zabezpieczeń ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)
- [Jak: Ustawianie strefy zabezpieczeń dla aplikacji ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)
- [Jak: Ustawianie uprawnień niestandardowych dla aplikacji ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Jak: Debugowanie aplikacji ClickOnce z ograniczonymi uprawnieniami](securing-clickonce-applications.md)
- [Jak: Dodawanie zaufanego wydawcy do komputera klienckiego dla aplikacji ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)
- [Jak: Konfigurowanie zachowania monitu zaufania ClickOnce](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)