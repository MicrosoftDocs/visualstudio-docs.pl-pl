---
title: Scenariusze instalacji pakietu VSPackage | Microsoft Docs
description: Zapoznaj się z najlepszymi rozwiązaniami dotyczącymi obsługi równoległych instalacji programu Visual Studio za pomocą współużytkowanych lub równoległych instalacji pakietu VSPackage.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSPackages, deployment considerations
author: acangialosi
ms.author: anthc
manager: jmartens
ms.workload:
- vssdk
ms.openlocfilehash: 81e298229bb12d906a3061e0b547553518cce204
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2021
ms.locfileid: "99900007"
---
# <a name="vspackage-setup-scenarios"></a>Scenariusze instalacji pakietu VSPackage

Ważne jest zaprojektowanie Instalatora pakietu VSPackage w celu zapewnienia elastyczności. Na przykład może być konieczne wydanie poprawki zabezpieczeń w przyszłości lub można zmienić strategię biznesową, która wymaga gruntownej obsługi wersji równoległych.

W przypadku [obsługi wielu wersji programu Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)można zapoznać się z zaletami i problemami z obsługą równoległych instalacji programu z [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] użyciem lub obok siebie instalacji pakietu VSPackage. Krótko mówiąc, obok siebie pakietów VSPackage zapewniają największą elastyczność obsługi nowych funkcji programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] .

Scenariusze omówione w tym temacie nie są jedynymi opcjami, ale są prezentowane jako sugerowane najlepsze rozwiązania.

## <a name="components-privacy-and-sharing"></a>Składniki, prywatność i udostępnianie

### <a name="make-your-components-independent"></a>Ustaw składniki jako niezależne

Po zidentyfikowaniu i wypełnieniu składnika, przypisaniu i `GUID` wdrożeniu składnika nie można zmienić jego kompozycji. Jeśli zmienisz kompozycję składnika, składnik wyniku musi być nowym składnikiem `GUID` . Uwzględniając te fakty, elastyczność zapewnia największą wersję, dzięki czemu każdy składnik jest niezależny od siebie jednostkowo. Aby uzyskać więcej informacji na temat reguł związanych ze składnikami, zobacz [zmiana kodu komponentu](/windows/desktop/Msi/changing-the-component-code) i [co się stanie, jeśli reguły składników są zerwane?](/windows/desktop/Msi/what-happens-if-the-component-rules-are-broken).

### <a name="do-not-mix-shared-and-private-resources-in-a-component"></a>Nie należy mieszać zasobów udostępnionych i prywatnych w składniku

Zliczanie odwołań odbywa się na poziomie składnika. W związku z tym mieszanie zasobów udostępnionych i prywatnych w jednym składniku uniemożliwia zaktualizowanie zasobów prywatnych, takich jak plik wykonywalny, bez konieczności zastępowania zasobów udostępnionych. W tym scenariuszu są tworzone problemy ze zgodnością z poprzednimi wersjami i uniemożliwiają tworzenie funkcji obok siebie.

Na przykład wartości rejestru używane do rejestrowania pakietu VSPackage z [!INCLUDE[vsipsdk](../../extensibility/includes/vsipsdk_md.md)] powinny być przechowywane w składniku innym niż używany do rejestrowania pakietu VSPackage w programie Visual Studio. Udostępnione pliki lub wartości rejestru przechodzą jeszcze przez inny składnik.

## <a name="scenario-1-shared-vspackage"></a>Scenariusz 1: Shared pakietu VSPackage

W tym scenariuszu udostępniony pakietu VSPackage (pojedynczy plik binarny obsługujący wiele wersji programu Visual Studio jest dostarczany w pakiecie Instalator Windows. Rejestrowanie w każdej wersji programu Visual Studio jest kontrolowane przez funkcje wybierane przez użytkownika. Oznacza to również, że po przypisaniu do oddzielnych funkcji każdy składnik można wybrać osobno w celu instalacji lub odinstalowania, co umożliwia użytkownikowi sterowanie integracją pakietu VSPackage z różnymi wersjami programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] . (Zobacz [Instalator Windows funkcje](/windows/desktop/Msi/windows-installer-features) , aby uzyskać więcej informacji na temat korzystania z funkcji w pakietach Instalator Windows).

![VS Shared pakietu VSPackage Installer](../../extensibility/internals/media/vs_sharedpackage.gif "VS_SharedPackage")

Jak pokazano na ilustracji, współdzielone składniki są częścią funkcji Feat_Common, która jest zawsze zainstalowana. Dzięki udostępnieniu Feat_VS2002 i Feat_VS2003 funkcji użytkownicy mogą wybrać w czasie instalacji, do których wersji programu Visual Studio chcą zintegrować pakietu VSPackage. Użytkownicy mogą również używać trybu konserwacji Instalator Windows, aby dodawać lub usuwać funkcje, co w tym przypadku dodaje lub usuwa informacje o rejestracji pakietu VSPackage z różnych wersji programu Visual Studio.

> [!NOTE]
> Ustawienie kolumny wyświetlania funkcji na 0 powoduje ukrycie jej. Wartość kolumny niskiego poziomu, na przykład 1, zapewnia, że będzie ona zawsze instalowana. Aby uzyskać więcej informacji, zobacz [INSTALLLEVEL właściwości](/windows/desktop/Msi/installlevel) i [funkcji tabeli](/windows/desktop/Msi/feature-table).

## <a name="scenario-2-shared-vspackage-update"></a>Scenariusz 2: współdzielona aktualizacja pakietu VSPackage

W tym scenariuszu jest wysyłana zaktualizowana wersja Instalatora pakietu VSPackage w scenariuszu 1. Na potrzeby dyskusji aktualizacja dodaje obsługę programu Visual Studio, ale może również być prostszym poprawkami zabezpieczeń lub błędem dodatku Service Pack. Reguły Instalator Windows instalowania nowszych składników wymagają, aby niezmienione składniki już w systemie nie były ponownie kopiowane. W takim przypadku system z wersją 1,0 już istnieje spowoduje zastąpienie zaktualizowanego składnika Comp_MyVSPackage.dll i umożliwienie użytkownikom dodania nowej funkcji Feat_VS2005 z jej składnikiem Comp_VS2005_Reg.

> [!CAUTION]
> Za każdym razem, gdy pakietu VSPackage jest współużytkowany między wieloma wersjami programu [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] , ważne jest, aby kolejne wydania pakietu VSPackage zachować zgodność z poprzednimi wersjami programu Visual Studio. Jeśli nie możesz zachować zgodności z poprzednimi wersjami, musisz użyć pakietów VSPackage prywatnego. Aby uzyskać więcej informacji, zobacz [Obsługa wielu wersji programu Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md).

![VS współużytkowany Instalator aktualizacji pakietu vs](../../extensibility/internals/media/vs_sharedpackageupdate.gif "VS_SharedPackageUpdate")

W tym scenariuszu jest wyświetlany nowy Instalator pakietu VSPackage, dzięki któremu można skorzystać z pomocy technicznej Instalator Windows w przypadku dodatkowych uaktualnień. Użytkownicy po prostu instalują wersję 1,1 i uaktualniają wersję 1,0. Nie jest jednak konieczne posiadanie wersji 1,0 w systemie. Ten sam Instalator zainstaluje wersję 1,1 w systemie bez wersji 1,0. Zaletą udostępniania drobnych uaktualnień w ten sposób jest to, że nie jest konieczne przechodzenie przez proces tworzenia Instalatora uaktualnienia i Instalatora w całym produkcie. Jeden Instalator wykonuje oba zadania. Poprawka zabezpieczeń lub dodatek Service Pack może zamiast tego wykorzystać zalety Instalator Windows poprawek. Aby uzyskać więcej informacji, zobacz [poprawek i uaktualnień](/windows/desktop/Msi/patching-and-upgrades).

## <a name="scenario-3-side-by-side-vspackage"></a>Scenariusz 3. pakietu VSPackage równoległe

Ten scenariusz przedstawia dwa Instalatory pakietu VSPackage — jedną dla każdej wersji programu Visual Studio .NET 2003 i Visual Studio. Każdy Instalator instaluje obok siebie lub prywatne pakietu VSPackage (jeden, który jest specjalnie zbudowany i instalowany dla określonej wersji programu Visual Studio). Każdy pakietu VSPackage jest w jego własnym składniku. W związku z tym każdy może być osobno serwisowany z poprawkami lub wersjami konserwacji. Ponieważ biblioteka DLL pakietu VSPackage jest teraz specyficzna dla wersji, można bezpiecznie uwzględnić informacje o rejestracji w tym samym składniku co Biblioteka DLL.

![Instalator pakietu vs Side-by-Side](../../extensibility/internals/media/vs_sbys_package.gif "VS_SbyS_Package")

Każdy Instalator zawiera również kod współużytkowany między dwoma instalatorami. Jeśli kod współużytkowany został zainstalowany w wspólnej lokalizacji, zainstalowanie obu plików. msi spowoduje zainstalowanie kodu udostępnionego tylko raz. Drugi Instalator po prostu zwiększa liczbę odwołań do składnika. Liczba odwołań gwarantuje, że jeśli jedna z pakietów VSPackage zostanie odinstalowana, udostępniony kod pozostanie dla innych pakietu VSPackage. Jeśli druga pakietu VSPackage jest również odinstalowywana, kod współużytkowany zostanie usunięty.

## <a name="scenario-4-side-by-side-vspackage-update"></a>Scenariusz 4: Aktualizacja pakietu VSPackage obok siebie

W tym scenariuszu pakietu VSPackage dla programu Visual Studio zostały poniesione z luki w zabezpieczeniach i trzeba wydać aktualizację. Tak jak w scenariuszu 2, można utworzyć nowy plik msi, który aktualizuje istniejącą instalację, aby uwzględnić poprawkę zabezpieczeń, a także wdrożyć nowe instalacje z poprawkami zabezpieczeń, które już istnieją.

W takim przypadku pakietu VSPackage jest zarządzanym pakietu vspackagem zainstalowanym w globalnej pamięci podręcznej zestawów (GAC). Podczas ponownego kompilowania programu w celu uwzględnienia poprawki zabezpieczeń należy zmienić część numeru wersji zestawu. Informacje rejestracyjne dla nowego numeru wersji zestawu zastępują poprzednią wersję, powodując [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] załadowanie stałego zestawu.

![Instalator aktualizacji pakietu programu vs Side-by-Side](../../extensibility/internals/media/vs_sbys_packageupdate.gif "VS_SbyS_PackageUpdate")

Aby uzyskać więcej informacji na temat wdrażania zestawów równoległych, zobacz [uproszczenie wdrażania i rozwiązywanie problemów z biblioteką DLL Hell przy użyciu .NET Framework](/previous-versions/dotnet/articles/ms973843(v=msdn.10)).

## <a name="see-also"></a>Zobacz też

- [Instalator Windows](/windows/desktop/Msi/windows-installer-portal)
- [Obsługiwanie wielu wersji programu Visual Studio](../../extensibility/supporting-multiple-versions-of-visual-studio.md)