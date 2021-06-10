---
title: Uwzględnij wymagania wstępne (aplikacja ClickOnce)
description: Dowiedz się, jak uzyskać pakiety instalatora dla wymagań wstępnych w celu rozpowszechniania aplikacji ClickOnce na komputerze dewelopera.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
author: mikejo5000
ms.author: mikejo
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: b41529182b7cca8cea8f94206601b7a818d35420
ms.sourcegitcommit: 6aa55db5e1fe19d4d17886e0bfe140dbd186f8ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/10/2021
ms.locfileid: "111877744"
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>Jak uwzględnić wymagania wstępne w aplikacji ClickOnce
Przed dystrybucją wstępnie wymaganego oprogramowania za pomocą aplikacji należy najpierw pobrać pakiety instalatora dla tych wymagań wstępnych [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] na komputer dewelopera. Po opublikowaniu aplikacji i wybraniu pozycji Pobierz wymagania wstępne z tej samej lokalizacji co moja aplikacja **wystąpi** błąd, jeśli pakietów instalatora nie ma w **folderze Pakiety.**

> [!NOTE]
> Aby dodać pakiet instalatora dla .NET Framework, zobacz .NET Framework Deployment Guide for Developers (Przewodnik wdrażania .NET Framework [dla deweloperów).](/dotnet/framework/deployment/deployment-guide-for-developers)

## <a name="to-add-an-installer-package-by-using-packagexml"></a><a name="Package"></a> Aby dodać pakiet instalatora przy użyciu Package.xml

1. W Eksplorator plików otwórz folder **Pakiety.**

    Domyślnie ścieżka to `%ProgramFiles(x86)%\Microsoft SDKs\ClickOnce Bootstrapper\Packages\` .

>[!NOTE]
> Począwszy od wersji Visual Studio 2019 Update 7 pakiety programu inicjujące będą również odnalezione w ścieżce *<VS Install Path> \MSBuild\Microsoft\VisualStudio\BootstrapperPackages.*

2. Otwórz folder dla wymagań wstępnych, które chcesz dodać, a następnie otwórz folder language dla zainstalowanej wersji programu (na przykład [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] **en** dla języka angielskiego).

3. W Notatniku otwórz *Package.xml* plik.

4. Znajdź element **Name** zawierający `http://go.microsoft.com/fwlink` element i skopiuj adres URL. Dołącz część **LinkID.**

   > [!NOTE]
   > Jeśli element **Name** nie zawiera elementu , otwórzProduct.xmlw folderze głównym dla wymagań wstępnych i znajdź `http://go.microsoft.com/fwlink` ciąg **fwlink.** 

   > [!IMPORTANT]
   > Niektóre wstępnie wymagane składniki mają wiele pakietów instalacyjnych (na przykład dla systemów 32-bitowych i 64-bitowych). Jeśli wiele **elementów name** zawiera **fwlink**, należy powtórzyć pozostałe kroki dla każdego z nich.

5. Wklej adres URL na pasku adresu przeglądarki, a następnie po wyświetleniu monitu o uruchomienie lub zapisanie wybierz pozycję **Zapisz.**

    W tym kroku plik instalatora jest pobierany na komputer.

6. Skopiuj plik do folderu głównego dla wstępnie wymaganego składnika.

    Na przykład w celu .NET Framework 4.7.2 skopiuj plik do *folderu \Packages\DotNetFX472.*

    Teraz można dystrybuować pakiet instalacyjny z aplikacją.

## <a name="see-also"></a>Zobacz też
- [How to: Install prerequisites with a ClickOnce application (Instaluj wymagania wstępne za pomocą aplikacji ClickOnce)](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
