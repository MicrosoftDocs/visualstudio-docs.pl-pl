---
title: Wybieranie między pakietami udostępnionymi i wersjonowanymi pakietami VSPackage | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 21fefb776fceeeef4db6997a5bd12a8b987af7d2
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80739885"
---
# <a name="choose-between-shared-and-versioned-vspackages"></a>Wybierz między pakietami współużytkowanymi i wersjonowanymi pakietami VSPackage
Różne wersje programu Visual Studio mogą współistnieć na tym samym komputerze. VSPackages może obsługiwać [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dowolną kombinację wersji.

 Można włączyć instalacje side-by-side vspackages za pomocą jednej z dwóch strategii, strategii udostępnionej lub strategii wersjonowane. Oba uwzględnić obecność wielu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wersji i skojarzonych wersji programu .NET Framework.

 W strategii udostępnionej jeden VSPackage jest zarejestrowany [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]do użytku w wielu wersjach programu . W strategii wersjonatumentów wiele bibliotek DLL vspackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] są zainstalowane, po jednym dla każdej wersji, które obsługujesz.

## <a name="shared-vspackages"></a>Udostępnione pakiety VSPackages
 Korzystanie z udostępnionego vspackage jest odpowiedni, gdy używasz [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]tego samego VSPackage w wielu wersjach programu . Aby zaimplementować udostępniony pakiet VSPackage, należy wykonać następujące kroki:

- Upewnij się, że vsPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]jest kompatybilny z wieloma wersjami programu . Dostępne są dwa sposoby:

  - Ogranicz swój vspackage do korzystania tylko [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] z funkcji najwcześniejszej wersji, która obsługujesz.

  - Program vspackage dostosować się do [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wersji, w której jest uruchomiony. Następnie, jeśli kwerendy dotyczące nowszych usług nie powiodą się, program [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]VSPackage może oferować inne usługi obsługiwane w starszych wersjach programu .

- Zarejestruj vsPackage odpowiednio. Aby uzyskać więcej informacji, zobacz [rejestracja vspackage](../extensibility/internals/vspackage-registration.md) i [zarządzana rejestracja VSPackage](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1).

- Odpowiednio zarejestruj rozszerzenia plików. Aby uzyskać więcej informacji, zobacz [Rejestrowanie rozszerzeń nazw plików dla wdrożeń side-by-side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).

- Utwórz instalatora, który wdraża pakiet VSPackage [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]dla odpowiednich wersji programu . Aby uzyskać więcej informacji, zobacz [Instalowanie pakietów VSPackages za pomocą Instalatora Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md) i [zarządzania składnikami](../extensibility/internals/component-management.md).

- Rozwiąj problem kolizji rejestracyjnych. Aby uzyskać więcej informacji, zobacz [rejestracja vspackage](../extensibility/internals/vspackage-registration.md).

- Upewnij się, że zarówno udostępnione, jak i wersjonowane pliki są zgodne z z licznymi odwołaniami, aby umożliwić bezpieczną instalację i usuwanie wielu wersji. Aby uzyskać więcej informacji, zobacz [Zarządzanie składnikami](../extensibility/internals/component-management.md).

## <a name="versioned-vspackages"></a>Pakiety VSPackages z wersją
 W ramach strategii VSPackage wersji, można utworzyć jeden [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] VSPackage dla każdej wersji, która obsługuje. W ten sposób jest to właściwe, gdy można [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]oczekiwać, aby skorzystać z usług świadczonych przez nowsze wersje programu , ponieważ każdy VSPackage może ewoluować bez wpływu na inne. Niemniej jednak wersjonowane strategii tworzenia wielu plików binarnych, albo z jednej bazy kodu lub z wielu niezależnych baz kodu, może pociągać za sobą więcej początkowego rozwoju niż strategii udostępnionej. Ponadto może być wymagana dodatkowa praca instalacjowa, ponieważ należy utworzyć oddzielną konfigurację [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dla każdej wersji lub pojedynczą konfigurację, która wykrywa wersje, które są zainstalowane i które obsługuje pakiet VSPackage.

## <a name="binary-compatibility"></a>Zgodność binarna
 Ogólnie rzecz biorąc zgodność binarna umożliwia vspackages kodu natywnego opracowanych z wcześniejszych wersji programu Visual Studio do uruchomienia w nowszych wersjach programu Visual Studio. Istnieją jednak trzy ważne wyjątki:

- Jeśli vspackage opiera się na określonej wersji środowiska wykonawczego języka wspólnego, [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] następnie należy określić, w której wersji jest uruchomiony.

- VsPackage może mieć zależność od określonej funkcji innego VSPackage lub innego produktu. W związku z tym VSPackage można uruchomić tylko wtedy, gdy zależność jest spełniony.

- Poprawka zabezpieczeń w dodatku [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] Service Pack lub nowszej wersji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]dodatku Service Pack może mieć wpływ na pakiet VSPackage. W takich przypadkach VSPackage opracowany z wcześniejszą wersją [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] może [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] nie działać w wersjach po zastosowaniu poprawki zabezpieczeń. Można jednak odbudować pakiet z nowszą wersją i uruchomić go również we wcześniejszych wersjach.

  Zarządzane pakiety VSPackages muszą [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] być [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] tworzone przy użyciu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]wersji i że pasują do docelowej wersji .

  Oprócz planowania zgodności binarnej dla plików binarnych VSPackage, należy również rozważyć formaty plików rozwiązania i projektu. Jeśli vsPackage tworzy nowy typ projektu, należy zdecydować, czy można go uruchomić [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]tylko w jednej wersji lub w wielu wersjach programu . Aby uzyskać więcej informacji, zobacz [Uaktualnianie projektów niestandardowych](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects).

## <a name="see-also"></a>Zobacz też
- [Instalowanie pakietów VSPackages za pomocą Instalatora Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md)
- [Zarządzanie komponentami](../extensibility/internals/component-management.md)
