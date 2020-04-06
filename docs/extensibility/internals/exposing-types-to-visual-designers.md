---
title: Wystawianie typów projektantom wizualizacji | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- types [Visual Studio SDK], exposing to visual designers
- designers [Visual Studio SDK], exposing types
- custom tools, exposing types to visual designers
ms.assetid: a7a32ad4-3a0a-4eb8-a6ac-491c42885639
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 9067f88b4bf1334e23a548bc6a2cbeb3eac6ad33
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80708440"
---
# <a name="expose-types-to-visual-designers"></a>Udostępnianie typów projektantom wizualnym
[!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]musi mieć dostęp do definicji klasy i typu w czasie projektowania, aby wyświetlić projektanta wizualnego. Klasy są ładowane ze wstępnie zdefiniowanego zestawu zestawów, które zawierają kompletny zestaw zależności bieżącego projektu (odwołania plus ich zależności). Może być również konieczne dla projektantów wizualnych, aby uzyskać dostęp do klas i typów, które są zdefiniowane w plikach generowanych przez narzędzia niestandardowe.

 Systemy [!INCLUDE[vbprvb](../../code-quality/includes/vbprvb_md.md)] [!INCLUDE[csprcs](../../data-tools/includes/csprcs_md.md)] i systemy projektu zapewniają obsługę uzyskiwania dostępu do wygenerowanych klas i typów za pośrednictwem tymczasowych przenośnych plików wykonywalnych (tymczasowych plików PDF). Dowolny plik wygenerowany przez narzędzie niestandardowe mogą być kompilowane do zestawu tymczasowego, tak aby typy mogą być ładowane z tych zestawów i narażone na projektantów. Dane wyjściowe każdego narzędzia niestandardowego jest kompilowany do oddzielnego tymczasowego PE, a powodzenie lub niepowodzenie tej kompilacji tymczasowej zależy tylko od tego, czy wygenerowany plik może być skompilowany. Mimo że projekt może nie zostać zbudowany jako całość, poszczególne tymczasowe PE mogą być nadal dostępne dla projektantów.

 System projektu zapewnia pełną obsługę śledzenia zmian w pliku wyjściowym narzędzia niestandardowego, pod warunkiem, że zmiany te są wynikiem uruchomienia narzędzia niestandardowego. Za każdym razem, gdy narzędzie niestandardowe jest uruchamiane, generowany jest nowy tymczasowy pe i odpowiednie powiadomienia są wysyłane do projektantów.

> [!NOTE]
> Ponieważ tymczasowy plik generowania wykonywalnego programu odbywa się w tle, żadne błędy nie są zgłaszane do użytkownika, jeśli kompilacja nie powiedzie się.

 Narzędzia niestandardowe korzystające z tymczasowej obsługi pe muszą być zgodne z następującymi regułami:

- **GeneratesDesignTimeSource** musi być ustawiona na 1 w rejestrze.

     Bez tego ustawienia nie ma kompilacji plików wykonywalnych programu.

- Wygenerowany kod musi być w tym samym języku co ustawienie projektu globalnego.

     Tymczasowy pe jest kompilowany niezależnie od tego, co narzędzie <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.DefaultExtension%2A> niestandardowe raportuje jako żądane rozszerzenie pod warunkiem, że **GeneratesDesignTimeSource** jest ustawiona na 1 w rejestrze. Rozszerzenie nie musi być *.vb*, *.cs*, lub *.jsl*; może to być dowolne rozszerzenie.

- Kod wygenerowany przez narzędzie niestandardowe musi być prawidłowy i musi być kompilowany samodzielnie przy <xref:Microsoft.VisualStudio.Shell.Interop.IVsSingleFileGenerator.Generate%2A> użyciu tylko zestaw odwołań obecnych w projekcie w momencie zakończenia wykonywania.

     Po skompilowaniu tymczasowego pe, jedynym plikiem źródłowym dostarczonym do kompilatora jest niestandardowe dane wyjściowe narzędzia. W związku z tym niestandardowe narzędzie, które używa tymczasowego PE musi generować pliki wyjściowe, które mogą być kompilowane niezależnie od innych plików w projekcie.

## <a name="see-also"></a>Zobacz też
- [Wprowadzenie do obiektu BuildManager](https://msdn.microsoft.com/library/50080ec2-c1c9-412c-98ef-18d7f895e7fa)
- [Wdrażanie generatorów pojedynczych plików](../../extensibility/internals/implementing-single-file-generators.md)
- [Rejestrowanie generatorów pojedynczych plików](../../extensibility/internals/registering-single-file-generators.md)
