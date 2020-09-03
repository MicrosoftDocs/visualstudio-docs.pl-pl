---
title: 'Instrukcje: uwzględnianie wymagań wstępnych z aplikacją ClickOnce | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-deployment
ms.topic: conceptual
ms.assetid: c66bf0a5-8c93-4e68-a224-3b29ac36fe4d
caps.latest.revision: 18
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.openlocfilehash: 9639da1f735095f6d04a59d1f2302f822423e006
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2020
ms.locfileid: "77557675"
---
# <a name="how-to-include-prerequisites-with-a-clickonce-application"></a>Porady: uwzględnianie wstępnie wymaganych składników w aplikacji ClickOnce
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Przed dystrybucją wstępnie wymaganego oprogramowania do [!INCLUDE[ndptecclick](../includes/ndptecclick-md.md)] aplikacji należy najpierw pobrać pakiety Instalatora dla tych wymagań wstępnych na komputer deweloperski. Gdy publikujesz aplikację i wybierzesz opcję **Pobierz wstępnie wymagane składniki z tej samej lokalizacji co moja aplikacja**, wystąpi błąd, jeśli pakiety Instalatora nie znajdują się w folderze **Packages** .  
  
> [!NOTE]
> Aby dodać pakiet Instalatora dla .NET Framework, zobacz [.NET Framework Przewodnik wdrażania dla deweloperów](/dotnet/framework/deployment/deployment-guide-for-developers).  
  
## <a name="to-add-an-installer-package-by-using-packagexml"></a><a name="Package"></a> Aby dodać pakiet Instalatora przy użyciu Package.xml  
  
1. W Eksploratorze plików otwórz folder **Packages** .  
  
     Domyślnie ścieżka to C:\Program Files\Microsoft Visual Studio 14.0 \ SDK\Bootstrapper\Packages w systemie 32-bitowym i C:\Program Files (x86) \Microsoft Visual Studio 14.0 \ SDK\Bootstrapper\Packages w systemie 64-bitowym.  
  
2. Otwórz folder dla wymagań wstępnych, które chcesz dodać, a następnie otwórz folder języka dla zainstalowanej wersji programu [!INCLUDE[vsprvs](../includes/vsprvs-md.md)] (na przykład **EN** for English).  
  
3. W Notatniku otwórz plik **Package.xml** .  
  
4. Znajdź element **name** , który zawiera `http://go.microsoft.com/fwlink` , i skopiuj adres URL. Uwzględnij część **LinkId** .  
  
    > [!NOTE]
    > Jeśli element **name** nie zawiera `http://go.microsoft.com/fwlink` , Otwórz plik **Product.xml** w folderze głównym dla wymagania wstępnego i Znajdź ciąg **fwlink** .  
  
    > [!IMPORTANT]
    > Niektóre wstępnie wymagane składniki mają wiele pakietów instalacyjnych (na przykład dla systemów 32-bitowych i 64-bitowych). Jeśli wiele elementów **nazwy** zawiera **fwlink**, należy powtórzyć pozostałe kroki dla każdego z nich.  
  
5. Wklej adres URL na pasku adresu przeglądarki, a następnie po wyświetleniu monitu o uruchomienie lub zapisanie wybierz pozycję **Zapisz**.  
  
     W tym kroku plik instalatora jest pobierany na komputer.  
  
6. Skopiuj plik do folderu głównego dla wstępnie wymaganego składnika.  
  
     Na przykład dla wstępnie wymaganego składnika Instalator Windows 4.5 skopiuj plik do folderu \Packages\WindowsInstaller4_5.  
  
     Teraz można dystrybuować pakiet instalacyjny z aplikacją.  
  
## <a name="see-also"></a>Zobacz też  
 [Porady: instalowanie wstępnie wymaganych składników za pomocą aplikacji ClickOnce](../deployment/how-to-install-prerequisites-with-a-clickonce-application.md)
