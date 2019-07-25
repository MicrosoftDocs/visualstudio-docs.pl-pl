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
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 3add6e3e4f38b5ba73cd5154720d7b283189526e
ms.sourcegitcommit: 85d66dc9fea3fa49018263064876b15aeb6f9584
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68461499"
---
# <a name="manage-assembly-and-manifest-signing"></a>Zarządzanie podpisywaniem zestawu i manifestu

Podpisywanie silnej nazwy daje składnikowi oprogramowania unikatowy identyfikator globalny. Silne nazwy są używane w celu zagwarantowania, że zestaw nie może być sfałszowany przez kogoś innego, i upewnić się, że zależności składników i instrukcje konfiguracji są mapowane na poprawną wersję składnika i składnika.

Silna nazwa składa się z tożsamości zestawu (prostej nazwy tekstu, numeru wersji i informacji o kulturze) oraz tokenu klucza publicznego i podpisu cyfrowego.

Aby uzyskać informacje na temat podpisywania zestawów w C# Visual Basic i projektach, zobacz [Tworzenie i używanie zestawów o silnej nazwie](/dotnet/framework/app-domains/create-and-use-strong-named-assemblies).

Aby uzyskać informacje na temat podpisywania zestawów C++ w projektach wizualnych, zobacz [zestawy oC++silnych nazwach (/CLI)](/cpp/dotnet/strong-name-assemblies-assembly-signing-cpp-cli).

> [!NOTE]
> Podpisywanie silnej nazwy nie chroni przed odtwarzaniem przez proces odtwarzania zestawu. Aby chronić przed odwróceniem, zobacz [społeczność Dotfuscator](dotfuscator/index.md).

## <a name="asset-types-and-signing"></a>Typy zasobów i podpisywanie

Można podpisywać zestawy .NET i manifesty aplikacji:

- Pliki wykonywalne ( *. exe*)

- Manifesty aplikacji ( *. exe. manifest*)

- Manifesty wdrożenia ( *. Application*)

- Współużytkowane zestawy składników ( *. dll*)

Podpisz następujące typy zasobów:

1. Zestawy, które mają zostać wdrożone w globalnej pamięci podręcznej zestawów (GAC).

2. Aplikacje ClickOnce i manifesty wdrożenia. Program Visual Studio umożliwia podpisywanie domyślnie dla tych aplikacji.

3. Podstawowe zestawy międzyoperacyjności, które są używane na potrzeby współdziałania modelu COM. Narzędzie TLBIMP wymusza silne nazewnictwo podczas tworzenia podstawowego zestawu międzyoperacyjnego na podstawie biblioteki typów modelu COM.

Ogólnie rzecz biorąc nie należy podpisywać plików wykonywalnych. Silnie nazwany składnik nie może odwoływać się do niesilnie nazwanego składnika wdrożonego z aplikacją. Program Visual Studio nie podpisuje plików wykonywalnych aplikacji, ale zamiast tego rejestruje manifest aplikacji, który wskazuje na plik wykonywalny o słabym kodzie. Należy unikać podpisywania składników, które są prywatne dla aplikacji, ponieważ podpisywanie może utrudniać zarządzanie zależnościami.

## <a name="how-to-sign-an-assembly-in-visual-studio"></a>Jak podpisać zestaw w programie Visual Studio

Aplikację lub składnik należy podpisać przy użyciu karty  podpisywanie okna właściwości projektu (kliknij prawym przyciskiem myszy węzeł projektu w **Eksplorator rozwiązań** i wybierz polecenie **Właściwości**). Wybierz kartę  podpisywanie, a następnie zaznacz pole wyboru **podpisz zestaw** .

Określ plik klucza. Jeśli zdecydujesz się utworzyć nowy plik klucza, nowe pliki kluczy są zawsze tworzone w formacie *PFX* . Musisz mieć nazwę i hasło dla nowego pliku.

> [!WARNING]
> Należy zawsze chronić plik klucza przy użyciu hasła, aby uniemożliwić innym osobom korzystanie z niego. Klucze można także zabezpieczyć za pomocą dostawców lub magazynów certyfikatów.

Możesz również wskazać klucz, który został już utworzony. Aby uzyskać więcej informacji na temat tworzenia kluczy, zobacz [Tworzenie pary kluczy publiczny-prywatny](/dotnet/framework/app-domains/how-to-create-a-public-private-key-pair).

Jeśli masz tylko dostęp do klucza publicznego, możesz użyć podpisywania opóźnień, aby odroczyć przypisanie klucza. Aby włączyć podpisywanie opóźnień, należy zaznaczyć pole wyboru **Opóźnij tylko znak** . Projekt podpisany z opóźnieniem nie jest uruchomiony i nie można go debugować. Można jednak pominąć weryfikację podczas opracowywania przy użyciu [Narzędzia do silnej nazwy SN. exe](/dotnet/framework/tools/sn-exe-strong-name-tool) z `-Vr` opcją.

Aby uzyskać informacje na temat podpisywania manifestów [, zobacz How to: Podpisywanie aplikacji i manifestów](../ide/how-to-sign-application-and-deployment-manifests.md)wdrożenia.

## <a name="see-also"></a>Zobacz także

- [Zestawy o silnych nazwach](/dotnet/framework/app-domains/strong-named-assemblies)
- [Zestawy o silnych nazwach (C++/CLI)](/cpp/dotnet/strong-name-assemblies-assembly-signing-cpp-cli)
