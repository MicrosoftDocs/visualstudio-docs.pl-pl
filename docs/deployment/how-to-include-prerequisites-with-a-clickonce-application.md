---
title: Uwzględnij wymagania wstępne (Aplikacja ClickOnce)
description: Dowiedz się, jak pobrać pakiety Instalatora dotyczące wymagań wstępnych do dystrybucji dla aplikacji ClickOnce na komputerze deweloperskim.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: e9199bb720cb94bc949a04bd59d5d3b6527108ed
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2020
ms.locfileid: "94351196"
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>Instrukcje: uwzględnianie wymagań wstępnych z aplikacją ClickOnce
Przed dystrybucją wstępnie wymaganego oprogramowania do [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji należy najpierw pobrać pakiety Instalatora dla tych wymagań wstępnych na komputer deweloperski. Gdy publikujesz aplikację i wybierzesz opcję **Pobierz wstępnie wymagane składniki z tej samej lokalizacji co moja aplikacja** , wystąpi błąd, jeśli pakiety Instalatora nie znajdują się w folderze **Packages** .

> [!NOTE]
> Aby dodać pakiet Instalatora dla .NET Framework, zobacz [.NET Framework Przewodnik wdrażania dla deweloperów](/dotnet/framework/deployment/deployment-guide-for-developers).

## <a name="to-add-an-installer-package-by-using-packagexml"></a><a name="Package"></a> Aby dodać pakiet Instalatora przy użyciu Package.xml

1. W Eksploratorze plików otwórz folder **Packages** .

    Ścieżka jest domyślnie `%ProgramFiles(x86)%\Microsoft SDKs\ClickOnce Bootstrapper\Packages\` .

2. Otwórz folder dla wymagań wstępnych, które chcesz dodać, a następnie otwórz folder języka dla zainstalowanej wersji programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (na przykład **EN** for English).

3. W Notatniku otwórz plik *Package.xml* .

4. Znajdź element **name** , który zawiera `http://go.microsoft.com/fwlink` , i skopiuj adres URL. Uwzględnij część **LinkId** .

   > [!NOTE]
   > Jeśli element **name** nie zawiera `http://go.microsoft.com/fwlink` , Otwórz plik **Product.xml** w folderze głównym dla wymagania wstępnego i Znajdź ciąg **fwlink** .

   > [!IMPORTANT]
   > Niektóre wstępnie wymagane składniki mają wiele pakietów instalacyjnych (na przykład dla systemów 32-bitowych i 64-bitowych). Jeśli wiele elementów **nazwy** zawiera **fwlink** , należy powtórzyć pozostałe kroki dla każdego z nich.

5. Wklej adres URL na pasku adresu przeglądarki, a następnie po wyświetleniu monitu o uruchomienie lub zapisanie wybierz pozycję **Zapisz**.

    W tym kroku plik instalatora jest pobierany na komputer.

6. Skopiuj plik do folderu głównego dla wstępnie wymaganego składnika.

    Na przykład dla wymagania wstępnego Instalator Windows 4,5 skopiuj plik do folderu *\packages\ WindowsInstaller4_5* .

    Teraz można dystrybuować pakiet instalacyjny z aplikacją.

## <a name="see-also"></a>Zobacz też
- [Instrukcje: instalowanie wstępnie wymaganych składników za pomocą aplikacji ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
