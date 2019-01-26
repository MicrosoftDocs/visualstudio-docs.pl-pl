---
title: 'Instrukcje: Ponowne podpisywanie aplikacji i manifestów wdrożenia | Dokumentacja firmy Microsoft'
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
ms.openlocfilehash: ba021e15e78f2a139cace9059187374ae39afe71
ms.sourcegitcommit: 2193323efc608118e0ce6f6b2ff532f158245d56
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/25/2019
ms.locfileid: "54947520"
---
# <a name="how-to-re-sign-application-and-deployment-manifests"></a>Instrukcje: Ponowne podpisywanie manifestów aplikacji i wdrożenia
Po wprowadzeniu zmian do właściwości wdrożenia w manifeście aplikacji dla aplikacji Windows Forms, aplikacji Windows Presentation Foundation (xbap) lub rozwiązań pakietu Office, musisz ją ponownie podpisać zarówno aplikację i manifesty wdrożenia za pomocą certyfikat. Ten proces pozwala upewnić się, że zmodyfikowany pliki nie są zainstalowane na komputerach użytkowników końcowych.  
  
 Inny scenariusz, w którym może ponownie podpisać manifesty jest, gdy Twoi klienci wymagają podpisać aplikację i manifesty wdrożenia za pomocą ich własnych certyfikatów.  
  
## <a name="re-sign-the-application-and-deployment-manifests"></a>Ponowne podpisywanie aplikacji i manifestów wdrożenia  
 W tej procedurze założono, że zostały już wprowadzone zmiany do pliku manifestu aplikacji (*.manifest*). Aby uzyskać więcej informacji, zobacz [jak: Zmień właściwości wdrożenia](https://msdn.microsoft.com/library/66052a3a-8127-4964-8147-2477ef5d1472).  
  
#### <a name="to-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Ponowne podpisywanie aplikacji i wdrażania manifestów za pomocą Mage.exe  
  
1.  Otwórz **Visual Studio Command Prompt** okna.  
  
2.  Zmień katalogi na folder, który zawiera pliki manifestu, które chcesz się zalogować.  
  
3.  Wpisz następujące polecenie, aby utworzyć plik manifestu aplikacji. Zastąp *ManifestFileName* z nazwą pliku manifestu, plus rozszerzenie. Zastąp *certyfikatu* ze ścieżką względną lub w pełni kwalifikowana plik certyfikatu i Zastąp *hasło* hasło dla certyfikatu.  
  
    ```cmd  
    mage -sign ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Na przykład można uruchomić następujące polecenie, aby podpisać manifest aplikacji dla dodatku, aplikacja formularza Windows lub aplikacji Windows Presentation Foundation przeglądarki. Certyfikaty tymczasowe, utworzone przez program Visual Studio nie są zalecane dla wdrożenia w środowisku produkcyjnym.  
  
    ```cmd  
    mage -sign WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -sign ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -sign WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
4.  Wpisz następujące polecenie, aby zaktualizować i podpisać plik manifestu wdrażania, zastępując nazw zastępczych, jak w poprzednim kroku.  
  
    ```cmd  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Na przykład można uruchomić następujące polecenie, aby zaktualizować i podpisać manifest wdrożenia dla dodatku programu Excel, aplikacji programu Windows Forms lub aplikacja przeglądarki Windows Presentation Foundation.  
  
    ```cmd  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  Opcjonalnie, skopiuj manifest wdrażania wzorca (*publikowania\\\<nazwa_aplikacji > .application*) do katalogu wdrażania wersji (*pliki publish\Application\\ \<nazwa_aplikacji > _\<wersji >*).  
  
## <a name="update-and-re-sign-the-application-and-deployment-manifests"></a>Aktualizowanie i ponowne podpisywanie manifestów aplikacji i wdrożenia  
 W tej procedurze założono, że zostały już wprowadzone zmiany do pliku manifestu aplikacji (*.manifest*), ale istnieją inne pliki, które zostały zaktualizowane. Podczas aktualizacji plików skrótu, który reprezentuje plik również musi zostać zaktualizowany.  
  
#### <a name="to-update-and-re-sign-the-application-and-deployment-manifests-with-mageexe"></a>Aktualizowanie i ponowne podpisywanie aplikacji i wdrażania manifestów za pomocą Mage.exe  
  
1.  Otwórz **Visual Studio Command Prompt** okna.  
  
2.  Zmień katalogi na folder, który zawiera pliki manifestu, które chcesz się zalogować.  
  
3.  Usuń *.deploy* rozszerzenie pliku z plików w Publikuj dane wyjściowe folderu.  
  
4.  Wpisz następujące polecenie, aby zaktualizować manifest aplikacji przy użyciu nowych skrótów do zaktualizowanych plików i podpisać plik manifestu aplikacji. Zastąp *ManifestFileName* z nazwą pliku manifestu, plus rozszerzenie. Zastąp *certyfikatu* ze ścieżką względną lub w pełni kwalifikowana plik certyfikatu i Zastąp *hasło* hasło dla certyfikatu.  
  
    ```cmd  
    mage -update ManifestFileName.manifest -CertFile Certificate -Password Password  
    ```  
  
     Na przykład można uruchomić następujące polecenie, aby podpisać manifest aplikacji dla dodatku, aplikacja formularza Windows lub aplikacji Windows Presentation Foundation przeglądarki. Certyfikaty tymczasowe, utworzone przez program Visual Studio nie są zalecane dla wdrożenia w środowisku produkcyjnym.  
  
    ```cmd  
    mage -update WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
5.  Wpisz następujące polecenie, aby zaktualizować i podpisać plik manifestu wdrażania, zastępując nazw zastępczych, jak w poprzednim kroku.  
  
    ```cmd  
    mage -update DeploymentManifest -appmanifest ApplicationManifest -CertFile Certificate -Password Password  
    ```  
  
     Na przykład można uruchomić następujące polecenie, aby zaktualizować i podpisać manifest wdrożenia dla dodatku programu Excel, aplikacji programu Windows Forms lub aplikacja przeglądarki Windows Presentation Foundation.  
  
    ```cmd  
    mage -update WindowsFormsApplication1.application -appmanifest WindowsFormsApplication1.exe.manifest -CertFile ..\WindowsFormsApplication1_TemporaryKey.pfx  
    mage -update ExcelAddin1.vsto -appmanifest ExcelAddin1.dll.manifest -CertFile ..\ExcelAddIn1_TemporaryKey.pfx  
    mage -update WpfBrowserApplication1.xbap -appmanifest WpfBrowserApplication1.exe.manifest -CertFile ..\WpfBrowserApplication1_TemporaryKey.pfx  
    ```  
  
6.  Dodaj *.deploy* rozszerzenie pliku do plików, z wyjątkiem pliki manifestu aplikacji i wdrożenia.  
  
7.  Opcjonalnie, skopiuj manifest wdrażania wzorca (*publikowania\\\<nazwa_aplikacji > .application*) do katalogu wdrażania wersji (*pliki publish\Application\\ \<nazwa_aplikacji > _\<wersji >*).  
  
## <a name="see-also"></a>Zobacz także  
 [Zabezpieczanie aplikacji ClickOnce](../deployment/securing-clickonce-applications.md)   
 [Zabezpieczenia dostępu kodu dla aplikacji ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)   
 [ClickOnce i podpis Authenticode](../deployment/clickonce-and-authenticode.md)   
 [Przegląd wdrażania zaufanych aplikacji](../deployment/trusted-application-deployment-overview.md)   
 [Instrukcje: Włączenie ustawień zabezpieczeń technologii ClickOnce](../deployment/how-to-enable-clickonce-security-settings.md)   
 [Instrukcje: Ustawienie strefy zabezpieczeń dla aplikacji ClickOnce](../deployment/how-to-set-a-security-zone-for-a-clickonce-application.md)   
 [Instrukcje: Ustawienie uprawnień niestandardowych dla aplikacji ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)   
 [Instrukcje: Debugowanie aplikacji ClickOnce z ograniczonymi uprawnieniami](../deployment/how-to-debug-a-clickonce-application-with-restricted-permissions.md)   
 [Instrukcje: Dodawanie zaufanego wydawcy do komputera klienckiego dla aplikacji ClickOnce](../deployment/how-to-add-a-trusted-publisher-to-a-client-computer-for-clickonce-applications.md)   
 [Instrukcje: Konfigurowanie funkcji ClickOnce zaufania monitowania](../deployment/how-to-configure-the-clickonce-trust-prompt-behavior.md)