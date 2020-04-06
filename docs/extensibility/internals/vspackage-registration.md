---
title: Rejestracja VSPackage | Dokumenty firmy Microsoft
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- registration, VSPackages
- VSPackages, registering
ms.assetid: ecd20da8-b04b-4141-a8f4-a2ef91dd597a
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: a05dec8fbef40143f31f2c0ac484824717ea2e32
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/06/2020
ms.locfileid: "80703921"
---
# <a name="vspackage-registration"></a>Rejestracja pakietu VSPackage
VsPackages musi [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] poinformować, że są one zainstalowane i powinny być ładowane. Ten proces odbywa się przez zapisanie informacji w rejestrze. Jest to typowe zadanie instalatora.

> [!NOTE]
> Jest to przyjęta praktyka podczas rozwoju VSPackage do korzystania z rejestracji własnej. Jednak [!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)] partnerzy nie mogą wysyłać swoich produktów przy użyciu rejestracji własnej w ramach konfiguracji.

 Wpisy rejestru w pakiecie Instalatora Windows są zazwyczaj dokonywane w tabeli Rejestru. Rozszerzenia plików można również rejestrować w tabeli Rejestr. Instalator Windows zapewnia jednak wbudowaną obsługę za pośrednictwem programowego identyfikatora (ProgId), tabel klas, rozszerzeń i zleceń. Aby uzyskać więcej informacji, zobacz [Tabele bazy danych](/windows/desktop/Msi/database-tables).

 Upewnij się, że wpisy rejestru są skojarzone ze składnikiem, który jest odpowiedni dla wybranej strategii side-by-side. Na przykład wpisy rejestru dla udostępnionego pliku powinny być skojarzone ze składnikiem Instalatora Windows tego pliku. Podobnie wpisy rejestru dla pliku specyficznego dla wersji powinny być skojarzone ze składnikiem tego pliku. W przeciwnym razie zainstalowanie lub odinstalowanie [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] pakietu VSPackage dla jednej wersji może spowodować przerwanie vspackage w innych wersjach. Aby uzyskać więcej informacji, zobacz [Obsługa wielu wersji programu Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).

> [!NOTE]
> Najprostszym sposobem zarządzania rejestracją jest użycie tych samych danych w tych samych plikach zarówno do rejestracji dewelopera, jak i rejestracji w czasie instalacji. Na przykład niektóre narzędzia do tworzenia instalatorów mogą korzystać z pliku w formacie reg w czasie kompilacji. Jeśli deweloperzy utrzymują pliki reg dla własnego codziennego programowania i debugowanie, te same pliki mogą być automatycznie zawarte w instalatorze. Jeśli nie można automatycznie udostępniać danych rejestracyjnych, należy upewnić się, że kopia danych rejestracyjnych instalatora jest aktualna.

## <a name="registering-unmanaged-vspackages"></a>Rejestrowanie niezarządzanych pakietów VSPackages
 Niezarządzane pakiety VSPackages (w tym te generowane przez szablon pakietu programu Visual Studio) używają plików .rgs w stylu ATL do przechowywania informacji rejestracyjnych. Format pliku rgs jest specyficzny dla ATL i zazwyczaj nie może być zużywany w stanie as-is przez narzędzie do tworzenia instalacji. Informacje rejestracyjne instalatora VSPackage muszą być przechowywane oddzielnie. Na przykład deweloperzy mogą przechowywać pliki w formacie reg w synchronizacji ze zmianami w plikach rgs. Pliki .reg mogą być scalane z RegEdit do pracy deweloperskich lub używane przez instalatora.

## <a name="registering-managed-vspackages"></a>Rejestrowanie zarządzanych pakietów VSPackages
 Narzędzie RegPkg odczytuje atrybuty rejestracji z zarządzanego programu VSPackage i może zapisywać informacje bezpośrednio w rejestrze lub zapisywać pliki w formacie reg, które mogą być używane przez instalatora.

> [!NOTE]
> Narzędzie RegPkg nie jest redystrybucyjne i nie może być używane do rejestrowania pakietu VSPackage w systemie użytkownika.

## <a name="why-vspackages-should-not-self-register-at-install-time"></a>Dlaczego VSPackages nie powinien samodzielnie zarejestrować się w czasie instalacji
 Instalatorzy VSPackage nie powinni polegać na samorewolucji. Na pierwszy rzut oka, utrzymanie vsPackage wartości rejestru tylko w VSPackage się wydaje się dobrym pomysłem. Biorąc pod uwagę, że deweloperzy potrzebują wartości rejestru dostępne dla ich rutynowej pracy i testowania, warto unikać utrzymywania oddzielnej kopii danych rejestru w instalatorze. Instalator może polegać na VSPackage się do zapisu wartości rejestru.

 Chociaż jest dobry w teorii, samorejestracji ma kilka wad, które sprawiają, że nie nadaje się do instalacji VSPackage:

- Poprawne obsługa instalacji, dezinstalacji, wycofywania instalacji i wycofywania dezinstalacji wymaga autora czterech akcji niestandardowych dla każdego zarządzanego programu VSPackage, który rejestruje się samodzielnie, wywołując regpkg.

- Twoje podejście do obsługi side-by-side może wymagać, aby być autorem czterech akcji niestandardowych, [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]które wywołują RegSvr32 lub RegPkg dla każdej obsługiwanej wersji programu .

- Instalacja z modułami zarejestrowanymi samodzielnie nie może być bezpiecznie wycofana, ponieważ nie ma możliwości poinformowania, czy klucze zarejestrowane samodzielnie są używane przez inną funkcję lub aplikację.

- Samodzielnie zarejestrowane biblioteki DLL czasami łączą się z pomocniczymi bibliotekami DLL, które nie są obecne lub są niewłaściwą wersją. Natomiast Instalator Windows może rejestrować biblioteki DLL przy użyciu tabel rejestru bez zależności od bieżącego stanu systemu.

- Kod rejestracji własnej można odmówić dostępu do zasobów sieciowych, takich jak biblioteki typów, jeśli składnik jest określony jako run-from-source i jest wymieniony w tabeli SelfReg. Może to spowodować niepowodzenie instalacji składnika podczas instalacji administracyjnej.

## <a name="see-also"></a>Zobacz też
- [Instalator Windows](/windows/desktop/Msi/windows-installer-portal)
- [Rejestracja pakietu zarządzanego](https://msdn.microsoft.com/library/f69e0ea3-6a92-4639-8ca9-4c9c210e58a1)
