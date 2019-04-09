---
title: 'Instrukcje: Uwzględnianie wstępnie wymaganych składników w aplikacji ClickOnce | Dokumentacja firmy Microsoft'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: dcef749068dfb1f13e5b08160a70dda168b771ee
ms.sourcegitcommit: 36f5ffd6ae3215fe31837f4366158bf0d871f7a9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59232856"
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>Instrukcje: Uwzględnianie wstępnie wymaganych składników w aplikacji ClickOnce
Aby można było dystrybuować wstępnie wymagane oprogramowanie za pomocą [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplikacji, musisz najpierw pobrać pakiety instalacyjne tych wstępnie wymaganych składników na komputerze dewelopera. Po opublikowaniu aplikacji i wybraniu **Pobierz wstępnie wymagane składniki z tej samej lokalizacji co aplikację**, wystąpi błąd, jeśli pakiety instalacyjne nie są w **pakietów** folderu.

> [!NOTE]
>  Aby dodać pakiet instalacyjny dla programu .NET Framework, zobacz [.NET Framework — przewodnik wdrażania dla deweloperów](/dotnet/framework/deployment/deployment-guide-for-developers).

##  <a name="Package"></a> Aby dodać pakiet instalacyjny przy użyciu pliku Package.xml

1. W Eksploratorze plików otwórz **pakietów** folderu.

    Domyślna ścieżka to `%ProgramFiles(x86)%\Microsoft SDKs\ClickOnce Bootstrapper\Packages\`.

2. Otwórz folder wstępnie wymaganego składnika, który chcesz dodać, a następnie otwórz folder języka dla zainstalowanej wersji programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (na przykład **en** w języku angielskim).

3. Otwórz w Notatniku *Package.xml* pliku.

4. Znajdź **nazwa** element, który zawiera **http://go.microsoft.com/fwlink**, a następnie skopiuj adres URL. Obejmują **LinkID** części.

   > [!NOTE]
   >  Jeśli nie **nazwa** element zawiera **http://go.microsoft.com/fwlink**, otwórz **Product.xml** pliku w folderze głównym wstępnie wymaganego składnika i zlokalizuj **fwlink** ciągu.

   > [!IMPORTANT]
   >  Niektóre wstępnie wymagane składniki mają wiele pakietów instalacyjnych (na przykład dla systemów 32-bitowych i 64-bitowych). Jeśli wiele **nazwa** elementy zawierają **fwlink**, pozostałe kroki należy powtórzyć dla każdego z nich.

5. Wklej adres URL w pasku adresu przeglądarki, a następnie, gdy zostanie wyświetlony monit o uruchomienie lub zapisanie, wybierz **Zapisz**.

    W tym kroku plik instalatora jest pobierany na komputer.

6. Skopiuj plik do folderu głównego dla wstępnie wymaganego składnika.

    Na przykład dla wstępnie wymaganego programu Windows Installer 4.5 skopiuj plik do *\Packages\WindowsInstaller4_5* folderu.

    Teraz można dystrybuować pakiet instalacyjny z aplikacją.

## <a name="see-also"></a>Zobacz także
- [Instrukcje: Zainstaluj wymagania wstępne przy użyciu aplikacji ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
