pkgname=lsfg-vk-git
pkgver=r103.223f4ba
pkgrel=1
pkgdesc='This project brings Lossless Scalings Frame Generation to Linux!'
arch=(x86_64)
url='https://github.com/PancakeTAS/lsfg-vk'
license=(MIT)

makedepends=(base-devel clang llvm vulkan-headers cmake meson ninja git sdl3 glslang)

source=(
	"git+$url"
)

sha256sums=(
	'SKIP'
)

pkgver() {
	cd lsfg-vk
	printf "r%s.%s" "$(git rev-list --count HEAD)" "$(git rev-parse --short HEAD)"
}

build() {
	cd "${srcdir}/lsfg-vk"

	export CMAKE_INSTALL_PREFIX="${pkgdir}/usr/local"

	cmake -B build -G Ninja \
		-DCMAKE_BUILD_TYPE=Release \
		-DCMAKE_INSTALL_PREFIX=$CMAKE_INSTALL_PREFIX \
		-DCMAKE_INTERPROCEDURAL_OPTIMIZATION=ON \
		-DCMAKE_CXX_CLANG_TIDY=""

	cmake --build build
}

package() {
	cd "${srcdir}/lsfg-vk"

	cmake --install build
}

