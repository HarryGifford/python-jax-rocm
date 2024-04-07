# Maintainer: Harry Gifford <hegiax@outlook.com>
pkgname='python-jax-rocm-bin'
pkgver=0.4.25
pkgrel=1
pkgdesc='XLA library for JAX'
_srcname="jax-jaxlib-v${pkgver}"
arch=('x86_64')
url='https://github.com/ROCm/jax'
license=('Apache')
depends=(
    absl-py
    miopen
    python-jaxlib
    python-numpy
    python-opt_einsum
    python-scipy
    python-six
    python
    rccl
    rocm-hip-runtime
)
makedepends=(python-build python-installer python-wheel)
source=("${url}/archive/refs/tags/jaxlib-v${pkgver}.tar.gz")
b2sums=('62adc0b2a10923e4a28b9c73571683c8fa5e37b48a87779129fd8b158102529b44433380e158f8dc66813998d5fb72cc098c07ef56706ec33b647e5d07d0f86a')
conflicts=('python-jax')
provides=("python-jax=${pkgver}")

build() {
    cd "${srcdir}/${_srcname}"
    python -m build --wheel --no-isolation
}

package() {
    cd "${srcdir}/${_srcname}"
    python -m installer --destdir="$pkgdir" dist/*.whl
    install -vDm644 -t "${pkgdir}/usr/share/licenses/${pkgname}" LICENSE
}
