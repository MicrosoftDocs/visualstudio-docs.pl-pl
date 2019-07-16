---
title: Zarządzanie składnikami | Dokumentacja firmy Microsoft
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
caps.latest.revision: 14
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 56a110f382d0b182eed0ea1a95cd4dabf2877037
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "68191855"
---
# <a name="component-management"></a>Zarządzanie składnikami
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Jednostki zadań w Instalatorze Windows są określane jako składniki Instalatora Windows (czasami nazywany WICs lub po prostu składników). Identyfikator GUID identyfikuje każdy składnik WIC to podstawowa jednostka instalacji i zliczanie dla ustawień, które przy użyciu Instalatora Windows.  
  
 Chociaż kilka produktów można użyć, aby utworzyć Instalatora pakietu VSPackage, przyjęto korzystania z plików Instalatora Windows (msi). Podczas tworzenia Instalatora, musi poprawnie Zarządzanie wdrażaniem pliku, tak, aby zliczanie odwołań poprawnych odbywa się na cały czas. W związku z tym różne wersje produktu nie zakłócają lub włamanie wzajemnie się kombinacji instalacji i odinstalować scenariuszy.  
  
 W Instalatorze Windows zliczanie odwołań występuje na poziomie składnika. Należy uważnie organizowanie zasobów — pliki, wpisy rejestru i tak dalej — na składniki. Istnieją inne poziomy organizacji — takich jak moduły, funkcje i produkty — które mogą pomóc w różnych scenariuszach. Aby uzyskać więcej informacji, zobacz [podstawy Instalatora Windows](../../extensibility/internals/windows-installer-basics.md).  
  
## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>Wytyczne dotyczące tworzenia Instalatora w celu instalacji Side-by-side  
  
- Tworzenie plików i kluczy rejestru, które są współużytkowane przez wersje na ich własnych składniki.  
  
     Dzięki temu można łatwo korzystać z nich w następnej wersji. Na przykład bibliotek typów, które są zarejestrowane na całym świecie, plik rozszerzenia i inne elementy, zarejestrowane w kluczu HKEY_CLASSES_ROOT i tak dalej.  
  
- Grupy składników udostępnionych do modułów scalania oddzielne.  
  
     Ułatwia to tworzenie poprawnie na potrzeby przechodzenia do przodu side-by-side.  
  
- Zainstaluj udostępnione pliki i klucze rejestru przy użyciu tych samych składników Instalatora Windows w wersjach.  
  
     Jeśli używasz innego składnika, pliki i wpisy rejestru są odinstalowywane po odinstalowaniu jednej określonej wersji pakietu VSPackage, ale innego pakietu VSPackage nadal jest zainstalowany.  
  
- Nie należy mieszać wersjonowana i udostępnionych elementów w jednym składniku.  
  
     To sprawia, że niemożliwe do instalacji udostępnione elementy globalnej lokalizacji i wersjonowanych elementów do lokalizacje izolowanych.  
  
- Nie ma kluczy rejestru udostępnionego, które wskazują wersji plików.  
  
     Jeśli to zrobisz, klucze współużytkowane zostaną zastąpione po zainstalowaniu innej wersji pakietu VSPackage. Po usunięciu druga wersja pliku, do którego wskazuje klucz został usunięty.  
  
## <a name="see-also"></a>Zobacz też  
 [Wybieranie między udostępnionymi i Wersjonowanymi pakietami VSPackage](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Scenariusze instalacji pakietu VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)
