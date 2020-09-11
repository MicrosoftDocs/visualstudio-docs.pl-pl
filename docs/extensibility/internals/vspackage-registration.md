---
title: Rejestracja pakietu VSPackage | Microsoft Docs
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
ms.openlocfilehash: 5941a0bc5d9f9f983a616dcc22cf1260d0911fa8
ms.sourcegitcommit: 4b29efeb3a5f05888422417c4ee236e07197fb94
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/11/2020
ms.locfileid: "90012129"
---
# <a name="vspackage-registration"></a>Rejestracja pakietu VSPackage
Pakietów VSPackage musi poinformować [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , że są one zainstalowane i powinny zostać załadowane. Ten proces jest realizowany przez zapisanie informacji w rejestrze. Jest to typowe zadanie Instalatora.

> [!NOTE]
> Jest to zaakceptowane rozwiązanie podczas opracowywania pakietu VSPackage w celu korzystania z samorejestracji. Jednak [!INCLUDE[vsipprvsip](../../extensibility/includes/vsipprvsip_md.md)] partnerzy nie mogą dostarczać swoich produktów przy użyciu samorejestracji w ramach instalacji.

 Wpisy rejestru w pakiecie Instalator Windows są zwykle wprowadzane w tabeli rejestru. Można również zarejestrować rozszerzenia plików w tabeli rejestru. Jednak Instalator Windows zapewnia wbudowaną obsługę za pomocą tabel identyfikatorów programowych (ProgId), klas, rozszerzeń i zleceń. Aby uzyskać więcej informacji, zobacz [tabele bazy danych](/windows/desktop/Msi/database-tables).

 Upewnij się, że wpisy rejestru są skojarzone ze składnikiem odpowiednim dla wybranej strategii Side-by-side. Na przykład wpisy rejestru dla udostępnionego pliku powinny być skojarzone ze składnikiem Instalator Windows tego pliku. Podobnie wpisy rejestru dla pliku specyficznego dla wersji powinny być skojarzone ze składnikiem tego pliku. W przeciwnym razie Instalowanie lub odinstalowywanie pakietu VSPackage dla jednej wersji programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] może spowodować uszkodzenie pakietu VSPackage w innych wersjach. Aby uzyskać więcej informacji, zobacz [Obsługa wielu wersji programu Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).

> [!NOTE]
> Najprostszym sposobem zarządzania rejestracją jest użycie tych samych danych w tych samych plikach zarówno w przypadku rejestracji dla deweloperów, jak i rejestracji w czasie instalacji. Na przykład niektóre narzędzia programistyczne Instalatora mogą korzystać z pliku w formacie reg w czasie kompilacji. Jeśli deweloperzy przechowują pliki reg do własnych codziennych wdrożeń i debugowania, te same pliki mogą być automatycznie dołączane do Instalatora. Jeśli nie można automatycznie udostępnić danych rejestracji, należy się upewnić, że kopia danych rejestracyjnych Instalatora jest aktualna.

## <a name="registering-unmanaged-vspackages"></a>Rejestrowanie niezarządzanych pakietów VSPackage
 Niezarządzana pakietów VSPackage (w tym te wygenerowane przez szablon pakietu programu Visual Studio) w celu przechowywania informacji rejestracyjnych należy użyć plików RGS w stylu ATL. Format pliku. RGS jest specyficzny dla ATL i nie może być zwykle używany przez narzędzie do tworzenia instalacji. Informacje o rejestracji dla Instalatora pakietu VSPackage muszą być utrzymywane osobno. Na przykład deweloperzy mogą przechowywać pliki w formacie reg zsynchronizowane ze zmianami w pliku. RGS. Pliki reg można scalać z regedit do pracy programistycznej lub wykorzystać przez Instalatora.

## <a name="registering-managed-vspackages"></a>Rejestrowanie zarządzanego pakietów VSPackage
 Narzędzie RegPkg odczytuje atrybuty rejestracji z zarządzanego pakietu VSPackage i może zapisywać informacje bezpośrednio do rejestru lub zapisywać pliki. reg, które mogą być używane przez Instalatora.

> [!NOTE]
> Narzędzie RegPkg nie jest oddystrybuowane i nie można go użyć do zarejestrowania pakietu VSPackage w systemie użytkownika.

## <a name="why-vspackages-should-not-self-register-at-install-time"></a>Dlaczego pakietów VSPackage nie powinny być rejestrowane w czasie instalacji
 Instalatory pakietu VSPackage nie należy polegać na rejestracji samoobsługowej. Na pierwszy rzut oka, zachowując wartości rejestru pakietu VSPackage tylko w samej pakietu VSPackage, wygląda jak dobry pomysł. Mając na względzie, że deweloperzy potrzebują wartości rejestru dostępnych dla ich rutynowej pracy i testowania, warto unikać obsługi oddzielnej kopii danych rejestru w instalatorze. Instalator może polegać na pakietu VSPackage sam do zapisu wartości rejestru.

 Chociaż jest dobrym rozwiązaniem, samodzielna rejestracja ma kilka wad, które nie są odpowiednie do instalacji pakietu VSPackage:

- Prawidłowe podwyższenie poziomu instalacji, dezinstalacji, wycofywania instalacji i wycofania dezinstalacji wymaga utworzenia czterech akcji niestandardowych dla wszystkich zarządzanych pakietu VSPackage, które są rejestrowane przez wywoływanie RegPkg.

- Podejście do obsługi równoczesnej może wymagać utworzenia czterech akcji niestandardowych, które wywołują program RegSvr32 lub RegPkg dla każdej obsługiwanej wersji programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

- Nie można bezpiecznie cofnąć instalacji z użyciem modułów z własnym rejestracją, ponieważ nie ma możliwości wyznaczenia, czy klucze samozarejestrowane są używane przez inną funkcję lub aplikację.

- Własne zarejestrowane biblioteki DLL czasami łączą się z pomocniczymi bibliotekami DLL, które nie są obecne lub są nieprawidłową wersją. Z kolei Instalator Windows mogą rejestrować biblioteki DLL przy użyciu tabel rejestru bez zależności od bieżącego stanu systemu.

- Kod samodzielnej rejestracji można odmówić dostępu do zasobów sieciowych, takich jak biblioteki typów, jeśli składnik jest jednocześnie określony jako Run-from-Source i znajduje się w tabeli SelfReg. Może to spowodować niepowodzenie instalacji składnika podczas instalacji administracyjnej.

## <a name="see-also"></a>Zobacz także
- [Instalator Windows](/windows/desktop/Msi/windows-installer-portal)
- [Rejestracja pakietu zarządzanego](/previous-versions/bb166783(v=vs.100))