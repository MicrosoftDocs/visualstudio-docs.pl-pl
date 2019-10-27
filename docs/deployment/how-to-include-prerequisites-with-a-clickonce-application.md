---
title: 'Instrukcje: uwzględnianie wymagań wstępnych z aplikacją ClickOnce | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c6826ae1f957778ac6eea556fdbbe9589ab3390b
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2019
ms.locfileid: "72727905"
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>Instrukcje: uwzględnianie wymagań wstępnych z aplikacją ClickOnce
Aby można było dystrybuować wstępnie wymagane oprogramowanie za pomocą aplikacji [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)], należy najpierw pobrać pakiety Instalatora dla tych wymagań wstępnych na komputer deweloperski. Gdy publikujesz aplikację i wybierzesz opcję **Pobierz wstępnie wymagane składniki z tej samej lokalizacji co moja aplikacja**, wystąpi błąd, jeśli pakiety Instalatora nie znajdują się w folderze **Packages** .

> [!NOTE]
> Aby dodać pakiet Instalatora dla .NET Framework, zobacz [.NET Framework Przewodnik wdrażania dla deweloperów](/dotnet/framework/deployment/deployment-guide-for-developers).

## <a name="Package"></a>Aby dodać pakiet Instalatora przy użyciu pliku Package. XML

1. W Eksploratorze plików otwórz folder **Packages** .

    Domyślnie ścieżka jest `%ProgramFiles(x86)%\Microsoft SDKs\ClickOnce Bootstrapper\Packages\`.

2. Otwórz folder dla wymagania wstępnego, który chcesz dodać, a następnie otwórz folder języka dla zainstalowanej wersji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] (na przykład **EN** for English).

3. W Notatniku otwórz plik *Package. XML* .

4. Znajdź element **name** zawierający **http://go.microsoft.com/fwlink** i skopiuj adres URL. Uwzględnij część **LinkId** .

   > [!NOTE]
   > Jeśli element **name** nie zawiera **http://go.microsoft.com/fwlink** , Otwórz plik **Product. XML** w folderze głównym wymagania wstępnego i Znajdź ciąg **fwlink** .

   > [!IMPORTANT]
   > Niektóre wstępnie wymagane składniki mają wiele pakietów instalacyjnych (na przykład dla systemów 32-bitowych i 64-bitowych). Jeśli wiele elementów **nazwy** zawiera **fwlink**, należy powtórzyć pozostałe kroki dla każdego z nich.

5. Wklej adres URL na pasku adresu przeglądarki, a następnie po wyświetleniu monitu o uruchomienie lub zapisanie wybierz pozycję **Zapisz**.

    W tym kroku plik instalatora jest pobierany na komputer.

6. Skopiuj plik do folderu głównego dla wstępnie wymaganego składnika.

    Na przykład dla wymagania wstępnego Instalator Windows 4,5 skopiuj plik do folderu *\Packages\WindowsInstaller4_5* .

    Teraz można dystrybuować pakiet instalacyjny z aplikacją.

## <a name="see-also"></a>Zobacz także
- [Instrukcje: instalowanie wstępnie wymaganych składników za pomocą aplikacji ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
