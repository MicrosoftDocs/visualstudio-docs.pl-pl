---
title: Udostępnianie typów projektantów wizualnych | Dokumentacja firmy Microsoft
ms.custom: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.reviewer: ''
ms.suite: ''
ms.technology:
- vs-ide-sdk
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- types [Visual Studio SDK], exposing to visual designers
- designers [Visual Studio SDK], exposing types
- custom tools, exposing types to visual designers
ms.assetid: a7a32ad4-3a0a-4eb8-a6ac-491c42885639
caps.latest.revision: 12
ms.author: gregvanl
manager: ghogen
ms.openlocfilehash: c19fe00713bd328574e5a05cc6f6f3a60f18ddf9
ms.sourcegitcommit: af428c7ccd007e668ec0dd8697c88fc5d8bca1e2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/16/2018
ms.locfileid: "51791556"
---
# <a name="exposing-types-to-visual-designers"></a>Udostępnianie typów dla projektantów wizualnych
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

[!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] musi mieć dostęp do definicje klas i typów w czasie projektowania w celu wyświetlenia projektanta wizualnego. Klas są ładowane z wstępnie zdefiniowany zbiór zestawów, zawierające zestaw zależności pełny bieżący projekt (odwołania oraz ich zależności). Może być również konieczne dla projektantów wizualnych dostępu klas i typów, które są zdefiniowane w plikach wygenerowanych przez narzędzia niestandardowe.  
  
 [!INCLUDE[vbprvb](../../includes/vbprvb-md.md)] i [!INCLUDE[csprcs](../../includes/csprcs-md.md)] systemy projektu umożliwiają uzyskiwanie dostępu do wygenerowanych klas i typów poprzez tymczasowe przenośne pliki wykonywalne (PEs tymczasowe). Dowolny plik generowanych przez niestandardowe narzędzie może być kompilowane do zestawu tymczasowe tak, aby typy, które mogą być ładowane z tych zestawów i widoczne dla projektantów. Dane wyjściowe narzędzia niestandardowego jest skompilowany w oddzielnych tymczasowych i powodzenie lub niepowodzenie tej kompilacji tymczasowego zależy tylko określa, czy można kompilować wygenerowany plik. Mimo, że projekt może nie kompilować się jako całości, poszczególne PEs tymczasowe mogą być nadal dostępne do projektantów.  
  
 System projektu zapewnia pełną obsługę śledzenia zmian do pliku danych wyjściowych niestandardowego narzędzia, pod warunkiem, że te zmiany są wynikiem uruchomić narzędzie niestandardowe. Każdorazowo, gdy niestandardowe narzędzie jest uruchamiane, jest generowany nowy tymczasowych i odpowiedniego powiadomienia są wysyłane do projektantów.  
  
> [!NOTE]
>  Ponieważ plik wykonywalny Generowanie tymczasowego programu jest wykonywany w tle, nie błędy są zgłaszane dla użytkownika, jeśli kompilacja zakończy się niepowodzeniem.  
  
 Narzędzia niestandardowe łączące korzystając z tymczasowego obsługi PE, należy wykonać następujące reguły:  
  
-   `GeneratesDesignTimeSource` musi być równa 1 w rejestrze.  
  
     Nie kompilacji pliku wykonywalnego programu odbywa się bez tego ustawienia.  
  
-   Wygenerowany kod musi być w tym samym języku co ustawienie globalne projektu.  
  
     Tymczasowych jest kompilowany niezależnie od tego, narzędzie niestandardowe raporty jako żądane rozszerzenie w <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> pod warunkiem, że `GeneratesDesignTimeSource` jest ustawiona na 1 w rejestrze. Rozszerzenie musi być .vb, .cs lub .jsl; może to być dowolne inne rozszerzenie.  
  
-   Kod wygenerowany przez niestandardowe narzędzie musi być prawidłowy, i należy ją skompilować na swój własny zestaw odwołania się w projekcie używane w czasie <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> zakończy się wykonywanie.  
  
     Po skompilowaniu tymczasowych tylko plik źródłowy, podany w kompilatorze znajduje się dane wyjściowe narzędzia niestandardowego. W związku z tym niestandardowe narzędzie, które używa tymczasowych, należy wygenerować pliki wyjściowe, które można skompilować niezależnie od innych plików w projekcie.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do obiektu BuildManager](http://msdn.microsoft.com/en-us/50080ec2-c1c9-412c-98ef-18d7f895e7fa)   
 [Implementowanie generatorów jednoplikowych](../../extensibility/internals/implementing-single-file-generators.md)   
 [Określanie Namespace domyślnego projektu](../../misc/determining-the-default-namespace-of-a-project.md)   
 [Rejestrowanie generatorów jednoplikowych](../../extensibility/internals/registering-single-file-generators.md)

