---
title: Zarządzanie podpisywaniem zestawu i manifestu
ms.date: 02/17/2017
ms.technology: vs-ide-deployment
ms.topic: conceptual
helpviewer_keywords:
- manifests [Visual Studio]
- signing manifests [Visual Studio]
- application manifests [Visual Studio]
- assemblies [Visual Studio], signing
ms.assetid: 6c1ef36b-25f7-4ad0-b29a-51801b7a5420
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 4f13df00059523ca87e720a999c596e203b20e49
ms.sourcegitcommit: cc841df335d1d22d281871fe41e74238d2fc52a6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "75593684"
---
# <a name="manage-assembly-and-manifest-signing"></a>Zarządzanie podpisywaniem zestawu i manifestu

Podpisywanie silnej nazwy nadaje składnikowi oprogramowania globalnie unikatową tożsamość. Silne nazwy są używane do zagwarantowania, że zestaw nie może być sfałszowane przez kogoś innego i upewnij się, że zależności składnika i instrukcje konfiguracji map do poprawnej wersji składnika i składnika.

Silna nazwa składa się z tożsamości zestawu (prosta nazwa tekstowa, numer wersji i informacje o kulturze) oraz token klucza publicznego i podpis cyfrowy.

Aby uzyskać informacje na temat podpisywania zestawów w projektach języka Visual Basic i C#, zobacz [Tworzenie i używanie zestawów o silnych nazwach](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies).

Aby uzyskać informacje na temat podpisywania zestawów w projektach języka C++, zobacz [Zestawy o silnych nazwach (C++/CLI)](/cpp/dotnet/strong-name-assemblies-assembly-signing-cpp-cli).

> [!NOTE]
> Podpisywanie silnej nazwy nie chroni przed inżynierią odwrotną zestawu. Aby chronić przed inżynierią odwrotną, zobacz [Społeczność dotfuscatora](dotfuscator/index.md).

## <a name="asset-types-and-signing"></a>Typy zasobów i podpisywanie

Można podpisać zestawy .NET i manifesty aplikacji:

- Pliki wykonywalne (*.exe*)

- Manifesty aplikacji (*.exe.manifest*)

- Manifesty wdrażania (*.application*)

- Udostępnione złożenia komponentów (*.dll*)

Podpisz następujące typy zasobów:

1. Zestawy, jeśli chcesz wdrożyć je w globalnej pamięci podręcznej zestawów (GAC).

2. ClickOnce aplikacji i manifestów wdrażania. Visual Studio domyślnie umożliwia podpisywanie dla tych aplikacji.

3. Podstawowe zestawy międzyoperacyjne, które są używane do współdziałania COM. Narzędzie TLBIMP wymusza silne nazewnictwo podczas tworzenia podstawowego zestawu interop z biblioteki typu COM.

Ogólnie rzecz biorąc, nie należy podpisywać plików wykonywalnych. Składnik o silnie nazwany nie może odwoływać się do składnika o silnej nazwie, który jest wdrażany z aplikacją. Visual Studio nie podpisuje plików wykonywalnych aplikacji, ale zamiast tego podpisuje manifest aplikacji, który wskazuje na plik wykonywalny o słabym nazwie. Należy unikać podpisywania składników, które są prywatne dla aplikacji, ponieważ podpisywanie może utrudnić zarządzanie zależnościami.

## <a name="how-to-sign-an-assembly-in-visual-studio"></a>Jak podpisać zestaw w programie Visual Studio

Użytkownik podpisuje aplikację lub składnik przy użyciu karty **Podpisywanie** w oknie właściwości projektu (kliknij prawym przyciskiem myszy węzeł projektu w **Eksploratorze rozwiązań** i wybierz **polecenie Właściwości).** Zaznacz kartę **Podpisywanie,** a następnie zaznacz pole wyboru **Podpisz złożenie.**

Określ plik klucza. Jeśli zdecydujesz się utworzyć nowy plik klucza, nowe pliki kluczy są zawsze tworzone w formacie *.pfx.* Potrzebujesz nazwy i hasła do nowego pliku.

> [!WARNING]
> Zawsze należy chronić plik klucza hasłem, aby uniemożliwić innej osobie korzystanie z niego. Klucze można również zabezpieczyć za pomocą dostawców lub magazynów certyfikatów.

Można również wskazać klucz, który został już utworzony. Aby uzyskać więcej informacji na temat tworzenia kluczy, zobacz [Tworzenie pary kluczy publiczno-prywatnych](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair).

Jeśli masz tylko dostęp do klucza publicznego, możesz użyć opóźnienia podpisywania, aby odroczyć przypisanie klucza. Włącz podpisywanie z opóźnieniem, zaznaczając pole wyboru **Tylko znak Opóźnienie.** Projekt podpisany z opóźnieniem nie jest uruchamiany i nie można go debugować. Można jednak pominąć weryfikację podczas tworzenia, używając [narzędzia silnej nazwy Sn.exe](/dotnet/framework/tools/sn-exe-strong-name-tool) z `-Vr` opcją.

Aby uzyskać informacje na temat podpisywania manifestów, zobacz [Jak: Podpisywanie manifestów aplikacji i wdrażania](../ide/how-to-sign-application-and-deployment-manifests.md).

## <a name="see-also"></a>Zobacz też

- [Zestawy o silnych nazwach](/dotnet/framework/app-domains/strong-named-assemblies)
- [Zestawy o silnych nazwach (C++/CLI)](/cpp/dotnet/strong-name-assemblies-assembly-signing-cpp-cli)
