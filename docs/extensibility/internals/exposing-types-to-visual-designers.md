---
title: Udostępnianie typów projektantów wizualnych | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- types [Visual Studio SDK], exposing to visual designers
- designers [Visual Studio SDK], exposing types
- custom tools, exposing types to visual designers
ms.assetid: a7a32ad4-3a0a-4eb8-a6ac-491c42885639
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: ffd060ca442d0979c76781ae4467b28af69a42b3
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "63415207"
---
# <a name="expose-types-to-visual-designers"></a>Udostępnianie typów projektantów wizualnych
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] musi mieć dostęp do definicje klas i typów w czasie projektowania w celu wyświetlenia projektanta wizualnego. Klas są ładowane z wstępnie zdefiniowany zbiór zestawów, zawierające zestaw zależności pełny bieżący projekt (odwołania oraz ich zależności). Może być również konieczne dla projektantów wizualnych dostępu klas i typów, które są zdefiniowane w plikach wygenerowanych przez narzędzia niestandardowe.

 [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] i [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] systemy projektu umożliwiają uzyskiwanie dostępu do wygenerowanych klas i typów poprzez tymczasowe przenośne pliki wykonywalne (PEs tymczasowe). Dowolny plik generowanych przez niestandardowe narzędzie może być kompilowane do zestawu tymczasowe tak, aby typy, które mogą być ładowane z tych zestawów i widoczne dla projektantów. Dane wyjściowe narzędzia niestandardowego jest skompilowany w oddzielnych tymczasowych i powodzenie lub niepowodzenie tej kompilacji tymczasowego zależy tylko określa, czy można kompilować wygenerowany plik. Mimo, że projekt może nie kompilować się jako całości, poszczególne PEs tymczasowe mogą być nadal dostępne do projektantów.

 System projektu zapewnia pełną obsługę śledzenia zmian do pliku danych wyjściowych niestandardowego narzędzia, pod warunkiem, że te zmiany są wynikiem uruchomić narzędzie niestandardowe. Każdorazowo, gdy niestandardowe narzędzie jest uruchamiane, jest generowany nowy tymczasowych i odpowiedniego powiadomienia są wysyłane do projektantów.

> [!NOTE]
> Ponieważ plik wykonywalny Generowanie tymczasowego programu jest wykonywany w tle, nie błędy są zgłaszane dla użytkownika, jeśli kompilacja zakończy się niepowodzeniem.

 Narzędzia niestandardowe łączące korzystając z tymczasowego obsługi PE, należy wykonać następujące reguły:

- **GeneratesDesignTimeSource** musi być równa 1 w rejestrze.

     Nie kompilacji pliku wykonywalnego programu odbywa się bez tego ustawienia.

- Wygenerowany kod musi być w tym samym języku co ustawienie globalne projektu.

     Tymczasowych jest kompilowany niezależnie od tego, narzędzie niestandardowe raporty jako żądane rozszerzenie w <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> pod warunkiem, że **GeneratesDesignTimeSource** jest ustawiona na 1 w rejestrze. Rozszerzenie musi być *.vb*, *.cs*, lub *.jsl*; może być dowolnym rozszerzeniem.

- Kod wygenerowany przez niestandardowe narzędzie musi być prawidłowy, i należy ją skompilować na swój własny zestaw odwołania się w projekcie używane w czasie <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> zakończy się wykonywanie.

     Po skompilowaniu tymczasowych tylko plik źródłowy, podany w kompilatorze znajduje się dane wyjściowe narzędzia niestandardowego. W związku z tym niestandardowe narzędzie, które używa tymczasowych, należy wygenerować pliki wyjściowe, które można skompilować niezależnie od innych plików w projekcie.

## <a name="see-also"></a>Zobacz także
- [Wprowadzenie do obiektu BuildManager](https://msdn.microsoft.com/library/50080ec2-c1c9-412c-98ef-18d7f895e7fa)
- [Implementowanie generatorów jednoplikowych](../../extensibility/internals/implementing-single-file-generators.md)
- [Rejestrowanie generatorów jednoplikowych](../../extensibility/internals/registering-single-file-generators.md)