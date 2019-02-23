---
title: Wybieranie między udostępnionymi i Wersjonowanymi pakietami VSPackage | Dokumentacja firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- SxS
- side-by-side installation
- installation [Visual Studio SDK], side-by-side
ms.assetid: e3128ac3-2e92-48e9-87ab-3b6c9d80e8c9
author: gregvanl
ms.author: gregvanl
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 705fe42cf158992bb041ac9b75348f7b25945631
ms.sourcegitcommit: b0d8e61745f67bd1f7ecf7fe080a0fe73ac6a181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/22/2019
ms.locfileid: "56697510"
---
# <a name="choose-between-shared-and-versioned-vspackages"></a>Wybieranie między udostępnionymi i wersjonowanymi pakietami VSPackage
Różne wersje programu Visual Studio mogą współistnieć na tym samym komputerze. Pakietów VSPackage może obsługiwać dowolnej kombinacji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] wersji.

 Aby umożliwić instalacje side-by-side pakietów VSPackage przy użyciu jednej z dwóch strategii, udostępniony strategię lub numerów wersji strategii. Zarówno pomieścić obecności wielu wersji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i skojarzone wersje [!INCLUDE[dnprdnshort](../code-quality/includes/dnprdnshort_md.md)].

 W przypadku użycia udostępnionego strategii jednego pakietu VSPackage jest zarejestrowana do użycia w wielu wersji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. W określonej wersji strategii, wiele pakietu VSPackage biblioteki DLL są zainstalowane, jeden dla każdej wersji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] która jest obsługiwana.

## <a name="shared-vspackages"></a>Udostępnione pakietów VSPackage
 Za pomocą udostępnionego pakietu VSPackage jest odpowiednie, jeśli używasz tego samego pakietu VSPackage w wielu wersjach [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Aby zaimplementować udostępnionego pakietu VSPackage, należy wykonać następujące czynności:

- Dzięki Twojego pakietu VSPackage zgodny z wieloma wersjami [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Dostępne są tak zrobić na dwa sposoby:

  - Limit Twojego pakietu VSPackage za pomocą funkcji najstarszą wersję programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] która jest obsługiwana.

  - Usługi pakietu VSPackage, aby dostosować je do wersji programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] , w którym jest uruchomiona. Następnie, jeśli zapytania dla nowszej usługi nie powiedzie się, Twoje pakietu VSPackage zaoferować innych usług, które są obsługiwane w starszych wersjach programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

- Zarejestruj swoje pakietu VSPackage odpowiednio. Aby uzyskać więcej informacji, zobacz [Rejestracja pakietu VSPackage](../extensibility/internals/vspackage-registration.md) i [rejestracji zarządzanego pakietu VSPackage](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1).

- Rejestrowanie rozszerzeń plików odpowiednio. Aby uzyskać więcej informacji, zobacz [rejestrowanie rozszerzeń nazw plików dla wdrożeń side-by-side](../extensibility/registering-file-name-extensions-for-side-by-side-deployments.md).

- Utwórz Instalatora, który służy do wdrażania Twojego pakietu VSPackage dla odpowiedniej wersji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Aby uzyskać więcej informacji, zobacz [instalowanie pakietów VSPackage przy użyciu Instalatora Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md) i [Zarządzanie składnikami](../extensibility/internals/component-management.md).

- Rozwiązać problem kolizji rejestracji. Aby uzyskać więcej informacji, zobacz [Rejestracja pakietu VSPackage](../extensibility/internals/vspackage-registration.md).

- Upewnij się, że zarówno udostępnionymi i wersjonowanymi plikami przestrzegać zliczania odniesień, by umożliwić bezpieczne instalacji i usuwania wielu wersji. Aby uzyskać więcej informacji, zobacz [Zarządzanie składnikami](../extensibility/internals/component-management.md).

## <a name="versioned-vspackages"></a>Numerów wersji pakietów VSPackage
 W obszarze wersjonowany strategii pakietu VSPackage, tworzenie jednego pakietu VSPackage dla każdej wersji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] która jest obsługiwana. W ten sposób jest odpowiednie, jeśli zamierzasz korzystać z zalet usługi świadczone przez nowszych wersjach [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)], ponieważ każdego pakietu VSPackage można rozwijać bez wpływu na inne. Niemniej jednak wersjonowany strategii tworzenia wielu plików binarnych, od jednej bazy kodu lub wielu kod niezależny od podstaw, może być pociąga za sobą więcej początkowego projektowania niż udostępnionego strategii. Ponadto pracy dodatkowej konfiguracji mogą być wymagane, ponieważ należy utworzyć oddzielne ustawienia dla każdej wersji albo jednego Instalatora, który wykrywa wersje [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] są instalowane i obsługuje Twojego pakietu VSPackage.

## <a name="binary-compatibility"></a>Zgodność binarną
 Ogólnie rzecz biorąc zgodność binarną umożliwia pakietów VSPackage kodu macierzystego opracowany z wcześniejszymi wersjami programu Visual Studio do uruchamiania w nowszych wersjach programu Visual Studio. Istnieją trzy ważne wyjątki:

- Jeśli Twojego pakietu VSPackage zależy od konkretnej wersji środowiska uruchomieniowego języka wspólnego, a następnie należy określić, w jakiej wersji programu [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] jest uruchomiona.

- Pakietu VSPackage może mieć zależność w określonych funkcji, inny pakietu VSPackage lub innego produktu. W związku z tym pakietu VSPackage można uruchomić tylko wtedy, gdy zależność jest spełniony.

- Pakietu VSPackage może mieć wpływ poprawkę zabezpieczeń w [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] dodatku service pack lub nowsza wersja [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. W takich przypadkach pakietu VSPackage opracowanych przez starszą wersję [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] mogą nie zostać uruchomione w wersjach [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] po zastosowaniu poprawki zabezpieczeń. Można jednak ponownie pakiet przy użyciu nowszej wersji i jest również uruchomić w starszych wersjach.

  Zarządzane pakietów VSPackage muszą zostać skompilowane przy użyciu wersji [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] i [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] zgodnych wersję docelową [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)].

  Oprócz planowanie zgodność binarną dla plików binarnych pakietu VSPackage, należy również wziąć pod uwagę rozwiązanie i projekt formatów plików. Jeśli Twoje pakietu VSPackage tworzy nowy typ projektu, należy zdecydować, czy można wykonać w tylko jednej wersji lub w wielu wersjach [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Aby uzyskać więcej informacji, zobacz [Uaktualnianie projektów niestandardowych](../extensibility/internals/upgrading-projects.md#upgrading-custom-projects).

## <a name="see-also"></a>Zobacz także
- [Instalowanie pakietów VSPackage przy użyciu Instalatora Windows](../extensibility/internals/installing-vspackages-with-windows-installer.md)
- [Zarządzanie składnikami](../extensibility/internals/component-management.md)