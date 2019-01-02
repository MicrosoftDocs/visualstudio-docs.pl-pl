---
title: Zarządzanie składnikami | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- installation [Visual Studio SDK], components
- installation [Visual Studio SDK], file management
ms.assetid: 029bffa2-6841-4caa-a41a-442467e1aedc
author: gregvanl
ms.author: gregvanl
manager: douge
ms.workload:
- vssdk
ms.openlocfilehash: 31508fd720d1bf6695d6f735e57a829b72087ba9
ms.sourcegitcommit: 37fb7075b0a65d2add3b137a5230767aa3266c74
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/02/2019
ms.locfileid: "53917454"
---
# <a name="component-management"></a>Zarządzanie składnikami
Jednostki zadań w Instalatorze Windows są określane jako składniki Instalatora Windows (czasami nazywany WICs lub po prostu składników). Identyfikator GUID identyfikuje każdy składnik WIC to podstawowa jednostka instalacji i zliczanie dla ustawień, które przy użyciu Instalatora Windows.  
  
 Chociaż kilka produktów można użyć, aby utworzyć Instalatora pakietu VSPackage, przyjęto korzystanie z Instalatora Windows (*.msi*) plików. Podczas tworzenia Instalatora, musi poprawnie Zarządzanie wdrażaniem pliku, tak, aby zliczanie odwołań poprawnych odbywa się na cały czas. W związku z tym różne wersje produktu nie zakłócają lub włamanie wzajemnie się kombinacji instalacji i odinstalować scenariuszy.  
  
 W Instalatorze Windows zliczanie odwołań występuje na poziomie składnika. Należy uważnie organizowanie zasobów — pliki, wpisy rejestru i tak dalej — na składniki. Istnieją inne poziomy organizacji — takich jak moduły, funkcje i produkty — które mogą pomóc w różnych scenariuszach. Aby uzyskać więcej informacji, zobacz [podstawowe informacje dotyczące Instalatora Windows](../../extensibility/internals/windows-installer-basics.md).  
  
## <a name="guidelines-of-authoring-setup-for-side-by-side-installation"></a>Wytyczne dotyczące tworzenia Instalatora w celu instalacji side-by-side  
  
-   Tworzenie plików i kluczy rejestru, które są współużytkowane przez wersje na ich własnych składniki.  
  
     Dzięki temu można łatwo korzystać z nich w następnej wersji. Na przykład bibliotek typów, które są zarejestrowane na całym świecie, rozszerzenia plików, inne elementy, zarejestrowane w **HKEY_CLASSES_ROOT**i tak dalej.  
  
-   Grupy składników udostępnionych do modułów scalania oddzielne.  
  
     Ta strategia umożliwia tworzenie poprawnie na potrzeby instalacji side-by-side przenoszenie do przodu.  
  
-   Zainstaluj udostępnione pliki i klucze rejestru przy użyciu tych samych składników Instalatora Windows w wersjach.  
  
     Jeśli używasz innego składnika, pliki i wpisy rejestru są odinstalowywane po odinstalowaniu jednej określonej wersji pakietu VSPackage, ale innego pakietu VSPackage nadal jest zainstalowany.  
  
-   Nie należy mieszać wersjonowana i udostępnionych elementów w jednym składniku.  
  
     To sprawia, że niemożliwe do instalacji udostępnione elementy globalnej lokalizacji i wersjonowanych elementów do lokalizacje izolowanych.  
  
-   Nie ma kluczy rejestru udostępnionego, które wskazują wersji plików.  
  
     Jeśli to zrobisz, klucze współużytkowane zostaną zastąpione po zainstalowaniu innej wersji pakietu VSPackage. Po usunięciu druga wersja pliku, do którego wskazuje klucz został usunięty.  
  
## <a name="see-also"></a>Zobacz także  
 [Wybieranie między udostępnionymi i wersjonowanymi pakietami VSPackage](../../extensibility/choosing-between-shared-and-versioned-vspackages.md)   
 [Scenariusze instalacji pakietu VSPackage](../../extensibility/internals/vspackage-setup-scenarios.md)