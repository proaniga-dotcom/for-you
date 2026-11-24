"""
a bouquet, written in code.  (v2)


keys:  space = pause spin  |  + / - = spin speed  |  r = reverse  |  n = next message  |  q = quit

make it yours without touching the code (all optional):
    BOUQUET_TO="someone"              "for someone" glows above the bouquet
    BOUQUET_FROM="your name"          changes the signature
    BOUQUET_MESSAGE="one custom line" replaces the rotating messages
    BOUQUET_INTRO=0                   skip the blooming intro
    BOUQUET_FPS / BOUQUET_SPIN / BOUQUET_TILT / BOUQUET_CAMERA_DISTANCE

tip: make the terminal big (or zoom out with ctrl + minus) and the flowers get way more detailed.
"""
import math
import os
import random
import shutil
import sys
import textwrap
import time


def _env_float(name, default, minimum=None):
    try:
        value = float(os.getenv(name, default))
        if not math.isfinite(value):
            value = float(default)
    except (TypeError, ValueError):
        value = float(default)
    return max(minimum, value) if minimum is not None else value


def _env_text(name, default):
    value = os.getenv(name)
    return default if value is None else value


def _env_flag(name, default):
    value = os.getenv(name)
    if value is None:
        return default
    return value.strip().lower() not in ("0", "false", "no", "off", "")


TO_NAME = _env_text("BOUQUET_TO", "A")  
FROM_NAME = _env_text("BOUQUET_FROM", "Red Ivan Clay")
SIGNATURE = _env_text("BOUQUET_SIGNATURE", "this is what happens when i hyperfixate/get bored lmao by " + FROM_NAME + ",,,")


MESSAGES = [
    "If I had a single flower for every time I think about you, I could walk forever in my garden.",
    "A flower cannot blossom without sunshine, and a man cannot live without love.",
    "roses are #ff005f, violets are #af87ff, i built this whole bouquet in code because i was so very bored,,, argh",
    "no water, no sunlight, just a little python",
    "",
]
if os.getenv("BOUQUET_MESSAGE"):
    MESSAGES = [os.getenv("BOUQUET_MESSAGE")]


FPS = max(1, int(_env_float("BOUQUET_FPS", 24, 1)))
SPIN_SPEED = _env_float("BOUQUET_SPIN", 0.55)
TILT = _env_float("BOUQUET_TILT", 0.30)
CAM_DIST = _env_float("BOUQUET_CAMERA_DISTANCE", 4.0, 0.5)
INTRO = _env_flag("BOUQUET_INTRO", True)

NUM_HEARTS = 16
NUM_PETALS = 26
TYPE_CPS = 28.0  
HEART = "\u2665"


DAISY_WHITE = [244, 248, 251, 254, 255, 231]
ASTER = [54, 97, 103, 140, 183, 189]
ROSE_RED = [52, 88, 125, 161, 197, 204, 211]
ROSE_BLUSH = [95, 132, 175, 181, 217, 224, 231]
ROSE_PEACH = [130, 166, 172, 209, 215, 216, 223]
ROSE_LAV = [54, 97, 103, 140, 147, 183, 189]
ROSE_CORAL = [88, 124, 160, 166, 203, 209, 216]
SUN_PETAL = [130, 172, 178, 214, 220, 227]
SUN_CENTER = [52, 58, 94, 94, 130, 136]
GOLD_CENTER = [94, 136, 178, 214, 220]
SAKURA_PAL = [132, 168, 175, 211, 218, 224, 231]
SAKURA_CENTER = [89, 125, 162, 198, 223]
LILY_PINK = [89, 125, 161, 205, 211, 218, 225]
LILY_WHITE = [138, 181, 187, 224, 230, 231]
LILY_CENTER = [100, 136, 172, 214, 220]
TULIP_RED = [52, 88, 124, 160, 196, 203]
TULIP_PINK = [132, 168, 205, 211, 218, 225]
TULIP_YELLOW = [136, 178, 214, 220, 226, 229]
TULIP_PURPLE = [54, 91, 97, 134, 140, 183]
BLUE = [61, 68, 69, 75, 111, 117, 153]
LAVENDER = [54, 55, 97, 98, 134, 140, 183]
GREENS = [22, 28, 28, 34, 35, 71, 77, 114]
EUCALYPTUS = [22, 28, 29, 35, 65, 72, 107, 108, 114]
CORE_GREEN = [22, 22, 23, 28, 29, 34]
PAPER_PINK = [95, 132, 168, 174, 211, 217, 224]
PAPER_LAV = [97, 103, 140, 146, 183, 189, 225]
PAPER_CREAM = [101, 137, 144, 180, 187, 223, 230, 231]
TISSUE = [138, 175, 181, 218, 224, 225, 231]
TISSUE_LAV = [97, 103, 140, 147, 183, 189, 225]
RIBBON = [52, 88, 124, 160, 197, 204, 217, 231]
HEART_PRINT = [89, 125, 161, 197]
TWINE = [94, 137, 180, 223]
TAG_PAL = [137, 180, 187, 223, 230, 231]
CUT_END = [151, 187, 230]
HEART_COLORS = [161, 197, 204, 205, 211, 218]
PETAL_COLORS = [175, 211, 217, 218, 224, 225]
MSG_COLORS = [161, 168, 205, 211, 218, 225, 218, 211, 205, 168]

SHADE = ".:-=+*%@"
PETAL_SHADE = ".:+*#%"
CORE_SHADE = ".:-=+*"
PETAL_CHARS = ",'`."
RESET = "\033[0m"


PIVOT_Y = 0.22
TOP_Y = 1.06
INV_2PI = 1.0 / (2.0 * math.pi)
AMBIENT = 0.34  

_L = (-0.45, 0.6, 0.66)
_n = math.sqrt(sum(v * v for v in _L))
LX, LY, LZ = (v / _n for v in _L)

CEN = (0.0, 0.14, 0.0)  
DOME = 0.68  
CORE_R = 0.50  
NECK = (0.0, -0.10, 0.0)  
STEM_CUT = 0.24  


Y0, Y1, R0, R1 = -0.30, 0.30, 0.05, 0.44
KC = (R1 - R0) / (Y1 - Y0)
BY = -0.06  

ROSE, SUN, DAISY, SAKURA, LILY, TULIP, HYDRA = range(7)
RADIAL = {ROSE: 1.0, SUN: 0.99, DAISY: 0.98, SAKURA: 1.0, LILY: 1.04, TULIP: 1.10, HYDRA: 0.96}

SPEC = {
    ROSE: (0.0, 0.50, 0.0, 0.45, 0, None),
    SUN: (0.46, 0.50, 0.20, 0.10, 18, SUN_CENTER),
    DAISY: (0.30, 0.62, 0.15, 0.10, 13, GOLD_CENTER),
    SAKURA: (0.13, 0.56, 0.35, 0.05, 5, SAKURA_CENTER),
    LILY: (0.15, 0.50, 0.50, 0.10, 6, LILY_CENTER),
}
NTAB = 96



def norm(v):
    m = math.sqrt(v[0] ** 2 + v[1] ** 2 + v[2] ** 2) or 1.0
    return (v[0] / m, v[1] / m, v[2] / m)


def cross(a, b):
    return (a[1] * b[2] - a[2] * b[1], a[2] * b[0] - a[0] * b[2], a[0] * b[1] - a[1] * b[0])


def basis(axis):
    helper = (0.0, 1.0, 0.0) if abs(axis[1]) < 0.9 else (1.0, 0.0, 0.0)
    u = norm(cross(helper, axis))
    return u, cross(axis, u)


def add(p, d, k):
    return (p[0] + d[0] * k, p[1] + d[1] * k, p[2] + d[2] * k)


def dist(a, b):
    return math.sqrt((a[0] - b[0]) ** 2 + (a[1] - b[1]) ** 2 + (a[2] - b[2]) ** 2)


def palette_index(brightness, palette):
    """Return a valid palette index, even at brightness boundary values."""
    return min(len(palette) - 1, max(0, int(brightness * len(palette))))


def ease_out_back(x):
    x = min(1.0, max(0.0, x))
    c1 = 1.70158
    c3 = c1 + 1.0
    return 1.0 + c3 * (x - 1.0) ** 3 + c1 * (x - 1.0) ** 2


def _rot(v, ca, sa, ct, st):
    xr = v[0] * ca - v[2] * sa
    zr = v[0] * sa + v[2] * ca
    return xr, v[1] * ct - zr * st, v[1] * st + zr * ct


def cone_r(y):
    """Radius of the paper cone at height y (never thinner than the tip)."""
    return max(R0, R0 + KC * (y - Y0))


def on_cone(xo, y, lift):
    """Wrap a flat (x, y) spot at the front of the cone onto its surface."""
    rad = cone_r(y)
    phi = max(-1.5, min(1.5, xo / rad))
    sp, cp = math.sin(phi), math.cos(phi)
    return rad * sp, rad * cp + lift, norm((sp, -KC, cp))



class Flower:
    __slots__ = ("kind", "pos", "axis", "u", "v", "pal", "cpal", "R", "seed", "delay",
                 "reach", "tone", "cr", "base", "slope", "cup")

    def __init__(self, kind, pos, axis, pal, R, seed, delay):
        self.kind, self.pos, self.axis, self.pal, self.R = kind, pos, axis, pal, R
        self.seed, self.delay = seed, delay
        self.u, self.v = basis(axis)
        self.cr, self.base, self.slope, self.cup, petals, self.cpal = SPEC.get(
            kind, (0.0, 0.5, 0.0, 0.0, 0, None))
        self.reach, self.tone = _tables(kind, petals)


def _tables(kind, petals):
    """Petal outline (reach) and petal shading (tone) around the flower, as lookup tables."""
    reach, tone = [], []
    for i in range(NTAB):
        ph = (i + 0.5) / NTAB * 2 * math.pi
        r, tn = 1.0, 0.0
        if kind == ROSE:
            r = 0.90 + 0.10 * math.cos(5 * ph)
        elif kind in (DAISY, SUN):
            c = abs(math.cos(petals * ph / 2))
            r = 0.34 + 0.66 * c ** 1.2 if kind == DAISY else 0.52 + 0.48 * c ** 0.7
            tn = 0.14 * (c - 0.5)
        elif kind == SAKURA:
            pa = (ph * 5 / (2 * math.pi)) % 1.0
            r = 0.64 + 0.36 * max(0.0, math.sin(math.pi * pa)) ** 0.6
            dn = abs(pa - 0.5)
            if dn < 0.07:
                r -= 0.18 * (1 - dn / 0.07)  
            tn = -0.20 * math.exp(-((pa - 0.5) / 0.09) ** 2)
        elif kind == LILY:
            r = 0.28 + 0.72 * abs(math.cos(3 * ph)) ** 1.6
            tn = -0.22 * math.exp(-(math.sin(3 * ph) / 0.22) ** 2)
        reach.append(r)
        tone.append(tn)
    return reach, tone




class Scene:
    __slots__ = ("pts", "flowers", "babies", "sparkles", "flies", "stars", "K")


def build_scene(density=1.0):
    rnd = random.Random(21)
    K = max(0.6, min(1.6, density))

    def n1(n):
        return max(3, int(n * K))

    pts = []

    def P(x, y, z, n, pal, tone=0.0, two=True, ov=None, zb=0.0):
        pts.append((x, y, z, n[0], n[1], n[2], pal, tone, two, ov, zb))

 
    wish = []
    for pal in (ROSE_RED, ROSE_BLUSH, ROSE_PEACH, ROSE_LAV, ROSE_CORAL, ROSE_BLUSH, ROSE_RED, ROSE_PEACH):
        wish.append((ROSE, pal, 0.175))
    wish += [(SUN, SUN_PETAL, 0.21), (SUN, SUN_PETAL, 0.20)]
    for pal in (LILY_PINK, LILY_WHITE, LILY_PINK):
        wish.append((LILY, pal, 0.185))
    wish += [(SAKURA, SAKURA_PAL, 0.135)] * 5
    wish += [(DAISY, DAISY_WHITE, 0.125)] * 4 + [(DAISY, ASTER, 0.125)]
    for pal in (TULIP_RED, TULIP_PINK, TULIP_YELLOW, TULIP_PURPLE):
        wish.append((TULIP, pal, 0.13))
    wish += [(HYDRA, BLUE, 0.11)] * 3

   
    placed, slots = [], []
    shi = math.sin(math.radians(86))
    for idx in sorted(range(len(wish)), key=lambda i: -wish[i][2]):
        kind, pal, R = wish[idx]
        slo = math.sin(math.radians(40 if kind == TULIP else 12))
        factor, pos, d = 0.82, None, None
        for attempt in range(480):
            if attempt and attempt % 80 == 0:
                factor *= 0.92
            s = rnd.uniform(slo, shi)
            c = math.sqrt(1 - s * s)
            az = rnd.uniform(0, 2 * math.pi)
            d = (c * math.cos(az), s, c * math.sin(az))
            pos = add(CEN, d, DOME * RADIAL[kind] * rnd.uniform(0.97, 1.04))
            if all(dist(pos, q) >= factor * (R + Rq) for q, Rq in placed):
                break
        placed.append((pos, R))
        slots.append((kind, pal, R, pos, d))
    slots.sort(key=lambda s: s[4][1])  

    flowers = []
    for rank, (kind, pal, R, pos, d) in enumerate(slots):
        axis = norm((d[0] + rnd.uniform(-0.18, 0.18), d[1] + rnd.uniform(-0.08, 0.20),
                     d[2] + rnd.uniform(-0.18, 0.18)))
        
        base = add(pos, axis, -0.03)
        if base[1] > STEM_CUT:
            tcut = (base[1] - STEM_CUT) / (base[1] - NECK[1])
            ns = n1(22)
            for j in range(ns):
                tt = tcut * j / (ns - 1)
                P(base[0] + (NECK[0] - base[0]) * tt, base[1] + (NECK[1] - base[1]) * tt,
                  base[2] + (NECK[2] - base[2]) * tt, (axis[0], 0.0, axis[2]), GREENS, -0.25)
        if kind == HYDRA:  
            for _ in range(n1(70)):
                v = norm((rnd.gauss(0, 1), rnd.gauss(0, 1), rnd.gauss(0, 1)))
                q = add(pos, v, R * rnd.uniform(0.78, 1.0))
                P(q[0], q[1], q[2], v, BLUE, rnd.uniform(-0.1, 0.12), False, rnd.choice("*o+*"))
            continue
        flowers.append(Flower(kind, pos, axis, pal, R, rnd.uniform(0, 6.28),
                              0.45 + rank * 0.085 + rnd.uniform(0, 0.12)))

   
    def leaf(q, e, f, ln, wd, tone):
        n = norm(cross(e, f))
        for a, b in LEAF_OFFS:
            P(q[0] + e[0] * a * ln + f[0] * b * wd, q[1] + e[1] * a * ln + f[1] * b * wd,
              q[2] + e[2] * a * ln + f[2] * b * wd, n, EUCALYPTUS, tone - 0.10 + 0.10 * a - 0.05 * abs(b))

   
    for i in range(10):
        az = (i + rnd.uniform(0.0, 0.8)) / 10 * 2 * math.pi
        c, s = math.cos(az), math.sin(az)
        d = norm((c, rnd.uniform(0.15, 0.7), s))
        side = (-s, 0.0, c)
        base = (0.30 * c, 0.27, 0.30 * s)
        Ls, droop = rnd.uniform(0.42, 0.58), rnd.uniform(0.10, 0.22)

        def sp(u, base=base, d=d, Ls=Ls, droop=droop):
            return (base[0] + d[0] * Ls * u, base[1] + d[1] * Ls * u - droop * u * u, base[2] + d[2] * Ls * u)

        nst = n1(12)
        for j in range(nst):
            p = sp(j / (nst - 1))
            P(p[0], p[1], p[2], (c, 0.3, s), EUCALYPTUS, -0.2)
        for k in range(6):
            u = 0.28 + 0.12 * k
            p, p2 = sp(u), sp(min(1.0, u + 0.05))
            tang = norm((p2[0] - p[0], p2[1] - p[1], p2[2] - p[2]))
            for sgn in (-1, 1):
                e = norm((tang[0] + side[0] * sgn * 0.9, tang[1], tang[2] + side[2] * sgn * 0.9))
                f = norm(cross(e, (0.0, 1.0, 0.0)))
                if f == (0.0, 0.0, 0.0):
                    f = basis(e)[0]
                q = add(p, e, 0.03)
                leaf(q, e, f, 0.062 - 0.012 * k / 5, 0.034, rnd.uniform(-0.08, 0.08))

   
    for i in range(8):
        a = (i + 0.5) / 8 * 2 * math.pi + rnd.uniform(-0.1, 0.1)
        c, s = math.cos(a), math.sin(a)
        base = (0.30 * c, 0.27, 0.30 * s)
        d = norm((c, 0.30 + rnd.uniform(-0.1, 0.15), s))
        side = (-s, 0.0, c)
        n = norm(cross(side, d))
        Ll, W = rnd.uniform(0.30, 0.40), 0.075
        nu, nv = n1(24), n1(9) | 1
        for ti in range(nu):
            t = ti / (nu - 1)
            wid = W * math.sin(math.pi * t ** 0.85) * (1 + 0.10 * math.sin(26 * t))  
            for wi in range(nv):
                w = wi / (nv - 1) * 2 - 1
                rib = 0.22 if wi == nv // 2 else 0.0
                P(base[0] + d[0] * Ll * t + side[0] * wid * w + n[0] * 0.03 * w * w,
                  base[1] + d[1] * Ll * t - 0.16 * t * t + n[1] * 0.03 * w * w,
                  base[2] + d[2] * Ll * t + side[2] * wid * w + n[2] * 0.03 * w * w,
                  n, GREENS, rib - 0.28 - 0.15 * abs(w))

    
    for i in range(7):
        az = i / 7 * 2 * math.pi + rnd.uniform(-0.3, 0.3)
        el = math.radians(rnd.uniform(48, 80))
        d = (math.cos(el) * math.cos(az), math.sin(el), math.cos(el) * math.sin(az))
        bu, bv = basis(d)
        r_end = rnd.uniform(0.95, 1.07)
        for j in range(n1(14)):
            q = add(CEN, d, 0.45 + (r_end * 0.78 - 0.45) * j / (n1(14) - 1))
            P(q[0], q[1], q[2], (d[0], 0.0, d[2]), GREENS, -0.1)
        nb = n1(16)
        for j in range(nb):
            rr = r_end * 0.76 + (r_end - r_end * 0.76) * j / (nb - 1)
            for k in range(3):
                ang_k = k / 3 * 2 * math.pi + j * 1.7
                off = 0.013 * (1 - 0.5 * j / nb)
                q = add(add(add(CEN, d, rr), bu, off * math.cos(ang_k)), bv, off * math.sin(ang_k))
                P(q[0], q[1], q[2], d, LAVENDER, rnd.uniform(-0.1, 0.12), False, ";" if k else ":", 0.01)

   
    rings = n1(52)
    two_pi = 2 * math.pi
    for i in range(rings):
        t = i / (rings - 1)
        r = R0 + (R1 - R0) * t
        cnt = max(10, int(170 * r * K))
        for j in range(cnt):
            ph = (j + rnd.random() * 0.9) / cnt * two_pi
            c, s = math.cos(ph), math.sin(ph)
            cuff = t > 0.9
            rr = r * (1.0 + 0.05 * (0.3 + 0.7 * t) * math.sin(7 * ph + 1.3 * t))  
            if cuff:
                rr *= 1.0 + 0.08 * (t - 0.9) / 0.1  
            y = Y0 + (Y1 - Y0) * t + 0.045 * (abs(math.sin(5 * ph + 0.3)) - 0.55) * t ** 4  
            d = (ph - (0.7 + 2.1 * t) + math.pi) % two_pi - math.pi
            tone = 0.30 + 0.17 * math.cos(7 * ph + 1.3 * t) - 0.14 * (1 - t)
            if cuff:
                pal, tone = PAPER_CREAM, tone + 0.10
            elif abs(d) < 0.55:  
                pal = PAPER_LAV
                if abs(abs(d) - 0.55) < 0.05:
                    tone += 0.30
            else:
                pal = PAPER_PINK
            P(rr * c, y, rr * s, norm((c, -KC, s)), pal, tone)

    
    for k in range(7):
        t = 0.14 + 0.11 * k
        r = R0 + (R1 - R0) * t
        cnt = max(5, int(r * 17 * K))
        for j in range(cnt):
            ph = (j + 0.5 * (k % 2)) / cnt * two_pi
            d = (ph - (0.7 + 2.1 * t) + math.pi) % two_pi - math.pi
            if abs(d) < 0.68:
                continue
            c, s = math.cos(ph), math.sin(ph)
            rr = r * (1.0 + 0.05 * (0.3 + 0.7 * t) * math.sin(7 * ph + 1.3 * t)) * 1.012
            P(rr * c, Y0 + (Y1 - Y0) * t, rr * s, norm((c, -KC, s)), HEART_PRINT, 0.30, False, HEART, 0.03)

    
    def collar(ya, yb, ra, rb, nrings, k_cnt, pal, crink, rim_amp, phase):
        nr = n1(nrings)
        slope = (rb - ra) / (yb - ya)
        for i in range(nr):
            t = i / (nr - 1)
            r = ra + (rb - ra) * t ** 0.8
            cnt = max(10, int(k_cnt * r * K))
            for j in range(cnt):
                ph = (j + rnd.random()) / cnt * two_pi
                c, s = math.cos(ph), math.sin(ph)
                rr = r * (1.0 + crink * t * (math.sin(9 * ph + 3 * t + phase) + 0.5 * math.sin(23 * ph + phase)))
                y = ya + (yb - ya) * t + rim_amp * t ** 3 * (abs(math.sin(6.5 * ph + phase)) - 0.5)
                tone = 0.18 + 0.22 * math.cos(9 * ph + 3 * t + phase) + 0.10 * math.sin(23 * ph) - 0.10 * (1 - t)
                P(rr * c, y, rr * s, norm((c, -slope * 0.8, s)), pal, tone)

    collar(0.24, 0.45, 0.34, 0.66, 18, 120, TISSUE, 0.07, 0.07, 0.4)
    collar(0.24, 0.56, 0.32, 0.50, 14, 100, TISSUE_LAV, 0.06, 0.06, 2.0)

   
    br = cone_r(BY) + 0.012
    nb = n1(110)
    for j in range(nb):
        ph = j / nb * two_pi
        c, s = math.cos(ph), math.sin(ph)
        for dy in (-0.016, -0.005, 0.005, 0.016):
            rr = br + KC * dy
            P(rr * c, BY + dy, rr * s, (c, -0.1, s), RIBBON, 0.28 + 0.12 * math.sin(3 * ph) + (0.12 if dy == 0.005 else 0.0))

    k0y = BY
    k0z = cone_r(BY) + 0.03
    e1 = (1.0, 0.0, 0.0)
    e2 = norm((0.0, 1.0, KC))
    nB = norm((0.0, -KC, 1.0))

    def bow(xx, yy, h):
        return (xx * e1[0] + yy * e2[0] + nB[0] * h,
                k0y + xx * e1[1] + yy * e2[1] + nB[1] * h,
                k0z + xx * e1[2] + yy * e2[2] + nB[2] * h)

    L, W = 0.20, 0.075
    nu, nv = n1(24), n1(9)
    for side in (-1, 1):
        alpha = 0.42
        dx2, dy2 = side * math.cos(alpha), math.sin(alpha)
        px, py = -dy2, dx2
        for iu in range(nu):
            u = 0.06 + 0.94 * iu / (nu - 1)
            wv = W * max(0.0, math.sin(math.pi * u ** 0.8)) ** 0.8 * min(1.0, 0.35 + u * 1.2)
            for iv in range(nv):
                v = iv / (nv - 1) * 2 - 1
                xx = dx2 * L * u + px * wv * v
                yy = dy2 * L * u + py * wv * v
                tone = 0.26 - 0.34 * (1 - abs(v)) * math.sin(math.pi * u) + (0.10 if abs(v) > 0.8 else 0.0)
                p = bow(xx, yy, 0.010)
                P(p[0], p[1], p[2], nB, RIBBON, tone, True, None, 0.01)
    for i in range(6):  # the knot
        for j in range(6):
            p = bow((i / 5 * 2 - 1) * 0.030, (j / 5 * 2 - 1) * 0.026, 0.020)
            P(p[0], p[1], p[2], nB, RIBBON, 0.40 - 0.08 * j / 5, True, None, 0.02)

   
    for i in range(9):
        a = i / 9 * two_pi + rnd.uniform(-0.2, 0.2)
        ca_, sa_ = math.cos(a), math.sin(a)
        spread = rnd.uniform(0.02, 0.07)
        ey = -0.56 - rnd.uniform(0, 0.03)
        ns = n1(26)
        for j in range(ns):
            t = j / (ns - 1)
            rad = 0.02 + (spread - 0.02) * t
            P(rad * ca_, (Y0 + 0.04) + (ey - Y0 - 0.04) * t, rad * sa_, (ca_, 0.0, sa_), GREENS, 0.0)
        P(spread * ca_, ey, spread * sa_, (ca_, -1.0, sa_), CUT_END, 0.2, True, "o", 0.01)
    for yy in (-0.43, -0.445):
        for j in range(24):
            ph = j / 24 * two_pi
            P(0.055 * math.cos(ph), yy, 0.055 * math.sin(ph), (math.cos(ph), 0.0, math.sin(ph)), TWINE, 0.25, True, None, 0.02)

   
    babies = []  
    for _ in range(n1(130)):
        a = rnd.random() * two_pi
        el = rnd.uniform(0.15, 1.45)
        rr = rnd.uniform(0.62, 0.88)
        babies.append((rr * math.cos(a) * math.cos(el), CEN[1] + rr * math.sin(el),
                       rr * math.sin(a) * math.cos(el), rnd.uniform(0, 6.28)))
    sparkles = []
    for _ in range(40):
        a = rnd.random() * two_pi
        rr = rnd.uniform(0.80, 1.05)
        sparkles.append((rr * math.cos(a), rnd.uniform(-0.3, 1.0), rr * math.sin(a),
                         rnd.uniform(0, 6.28), rnd.uniform(1.5, 4.0)))
    flies = []  
    for _ in range(12):
        flies.append((rnd.uniform(0.85, 1.15), rnd.uniform(-0.2, 0.9), rnd.uniform(0.4, 0.9) * rnd.choice((-1, 1)),
                      rnd.uniform(0, 6.28)))
    stars = [(rnd.random(), rnd.random(), rnd.uniform(0, 6.28), rnd.uniform(0.6, 2.2)) for _ in range(70)]

    sc = Scene()
    sc.pts, sc.flowers, sc.babies, sc.sparkles, sc.flies, sc.stars, sc.K = pts, flowers, babies, sparkles, flies, stars, K
    return sc


LEAF_OFFS = [(-0.7, 0.0), (-0.3, -0.45), (-0.3, 0.0), (-0.3, 0.45),
             (0.1, -0.5), (0.1, 0.0), (0.1, 0.5), (0.5, 0.0)]


def dynamic_points(t, K):
    out = []
    nu, nv = max(8, int(24 * K)), max(3, int(5 * K))
    for side in (-1, 1):  
        for i in range(nu):
            u = i / (nu - 1)
            sway = 0.035 * math.sin(t * 1.7 + side * 0.9 + u * 2.0) * u
            xo = side * (0.040 + 0.065 * u) + sway
            y = BY - 0.045 - 0.30 * u
            for j in range(nv):
                v = j / (nv - 1) * 2 - 1
                if u > 1 - 0.14 * (1 - abs(v)):
                    continue
                x, z, nn = on_cone(xo + 0.020 * v, y, 0.016)
                out.append((x, y, z, nn[0], nn[1], nn[2], RIBBON, 0.28 + 0.2 * math.sin(5 * u + side) + 0.08 * (1 - abs(v)),
                            True, None, 0.015))
    nc = max(14, int(28 * K))
    for k in range(4):  
        side = -1 if k % 2 == 0 else 1
        ph0 = k * 1.3
        for i in range(nc):
            u = i / (nc - 1)
            sway = 0.03 * math.sin(t * 1.9 + k) * u
            xo = side * (0.050 + 0.05 * u + 0.012 * k) + 0.016 * math.sin(u * math.pi * 7 + ph0) * (0.3 + u) + sway
            y = BY - 0.05 - (0.20 + 0.03 * k) * u
            x, z, nn = on_cone(xo, y, 0.018 + 0.018 * math.cos(u * math.pi * 7 + ph0) * u)
            out.append((x, y, z, nn[0], nn[1], nn[2], RIBBON, 0.32 + 0.2 * math.cos(u * 20 + k), True, None, 0.02))
    
    th = 0.16 * math.sin(t * 1.25)
    ax, ay = math.sin(th), -math.cos(th)
    px, py = math.cos(th), math.sin(th)
    p0x, p0y, ls = 0.0, BY - 0.02, 0.07
    tx, ty = p0x + ax * ls, p0y + ay * ls
    for k in range(6):
        u = k / 5
        x, z, nn = on_cone(p0x + ax * ls * u, p0y + ay * ls * u, 0.040)
        out.append((x, p0y + ay * ls * u, z, nn[0], nn[1], nn[2], TWINE, 0.0, True, None, 0.01))
    hw, hh = 0.050, 0.068
    gx, gy = max(5, int(6 * K)), max(7, int(8 * K))
    for i in range(gx):
        for j in range(gy):
            qx = (i / (gx - 1) * 2 - 1) * hw
            qy = j / (gy - 1) * 2 * hh
            edge = i in (0, gx - 1) or j in (0, gy - 1)
            x, z, nn = on_cone(tx + px * qx + ax * qy, ty + py * qx + ay * qy, 0.046)
            out.append((x, ty + py * qx + ay * qy, z, nn[0], nn[1], nn[2], TAG_PAL, 0.0 if edge else 0.26,
                        True, None, 0.02))
    x, z, nn = on_cone(tx + ax * hh, ty + ay * hh, 0.046)
    out.append((x, ty + ay * hh, z, nn[0], nn[1], nn[2], HEART_PRINT, 0.5, False, HEART, 0.06))
    return out



def layout(cols, rows, msg_rows):
    view_rows = max(6, rows - msg_rows - 1)
    scale = max(1.0, min((view_rows - 2) / 1.80, (cols - 2) / 3.5))
    return view_rows, scale


def draw_core(cam, zbuf, chars, colors, view_rows, cols):
    ca, sa, ct, st, cx, cy, sxs, scale = cam
    x, y, z = CEN
    xr = x * ca - z * sa
    zr = x * sa + z * ca
    yp = y - PIVOT_Y
    yt = yp * ct - zr * st
    zt = yp * st + zr * ct
    f = CAM_DIST / (CAM_DIST - zt)
    fx, fy = cx + xr * f * sxs, cy - yt * f * scale
    rx, ry = CORE_R * f * sxs, CORE_R * f * scale
    for row in range(max(0, int(fy - ry) - 1), min(view_rows, int(fy + ry) + 2)):
        dy = (row + 0.5 - fy) / ry
        zrow, crow, clrow = zbuf[row], chars[row], colors[row]
        for col in range(max(0, int(fx - rx) - 1), min(cols, int(fx + rx) + 2)):
            dx = (col + 0.5 - fx) / rx
            q = dx * dx + dy * dy
            if q >= 1.0:
                continue
            nzv = math.sqrt(1.0 - q)
            zz = zt + CORE_R * nzv
            if zz <= zrow[col]:
                continue
            oy, oz = -dy * CORE_R, nzv * CORE_R
            yw = CEN[1] + oy * ct + oz * st
            if yw < 0.27:
                continue
            ox = dx * CORE_R
            zr2 = -oy * st + oz * ct
            xo = ox * ca + zr2 * sa
            zo = -ox * sa + zr2 * ca
            h = ((int((xo + 4) * 20) * 73856093) ^ (int((yw + 4) * 20) * 19349663)
                 ^ (int((zo + 4) * 20) * 83492791)) & 7
            dot = dx * LX - dy * LY + nzv * LZ
            b = 0.30 + 0.35 * max(0.0, dot) + (h - 3.5) * 0.035
            b = min(0.999, max(0.0, b))
            zrow[col] = zz
            crow[col] = CORE_SHADE[int(b * len(CORE_SHADE))]
            clrow[col] = CORE_GREEN[int(b * len(CORE_GREEN))]


def draw_points(plist, cam, zbuf, chars, colors, view_rows, cols):
    ca, sa, ct, st, cx, cy, sxs, scale = cam
    cam_dist, piv = CAM_DIST, PIVOT_Y
    lx, ly, lz = LX, LY, LZ
    shade, ns = SHADE, len(SHADE)
    for x, y, z, nx, ny, nz, pal, tone, two, ov, zb in plist:
        xr = x * ca - z * sa
        zr = x * sa + z * ca
        yp = y - piv
        yt = yp * ct - zr * st
        zt = yp * st + zr * ct
        f = cam_dist / (cam_dist - zt)
        col = int(cx + xr * f * sxs)
        row = int(cy - yt * f * scale)
        if row < 0 or row >= view_rows or col < 0 or col >= cols:
            continue
        zz = zt + zb
        zrow = zbuf[row]
        if zz <= zrow[col]:
            continue
        nxr = nx * ca - nz * sa
        nzr = nx * sa + nz * ca
        nyt = ny * ct - nzr * st
        nzt = ny * st + nzr * ct
        dot = nxr * lx + nyt * ly + nzt * lz
        if two and dot < 0:
            dot = -dot * 0.55
        b = AMBIENT + 0.70 * (dot if dot > 0.0 else 0.0) + tone
        b = 0.0 if b < 0.0 else (0.999 if b > 0.999 else b)
        zrow[col] = zz
        chars[row][col] = ov or shade[int(b * ns)]
        colors[row][col] = pal[int(b * len(pal))]


def raster_flower(fl, g, t, cam, zbuf, chars, colors, view_rows, cols):
    ca, sa, ct, st, cx, cy, sxs, scale = cam
    x, y, z = fl.pos
    xr = x * ca - z * sa
    zr = x * sa + z * ca
    yp = y - PIVOT_Y
    yt = yp * ct - zr * st
    zt = yp * st + zr * ct
    f = CAM_DIST / (CAM_DIST - zt)
    fx, fy = cx + xr * f * sxs, cy - yt * f * scale
    R = fl.R * g * (1.0 + 0.03 * math.sin(t * 1.6 + fl.seed))  
    dim = -0.4 * (1.0 - min(1.0, max(0.0, (zt + 0.6) / 1.2)))  
    pal = fl.pal
    npal = len(pal)
    Rx, Ry = R * f * sxs, R * f * scale
    PS, NP = PETAL_SHADE, len(PETAL_SHADE)

    if fl.kind == TULIP:  
        rx, ry = Rx * 0.8, Ry * 1.35
        if ry < 0.5:
            return
        for row in range(max(0, int(fy - ry) - 1), min(view_rows, int(fy + ry) + 2)):
            dy = (row + 0.5 - fy) / ry
            v = (1 - dy) / 2
            if v < 0 or v > 1:
                continue
            hw = 0.62 * math.sin(math.pi * 0.5 * min(1.0, v * 1.5 + 0.05))
            if hw <= 0:
                continue
            for col in range(max(0, int(fx - rx) - 1), min(cols, int(fx + rx) + 2)):
                dx = (col + 0.5 - fx) / rx
                if abs(dx) > hw:
                    continue
                xn = dx / hw
                if v > 0.72 + 0.28 * math.cos(1.5 * math.pi * xn) ** 2:
                    continue
                if zt + 0.03 <= zbuf[row][col]:
                    continue
                seam = -0.25 if abs(abs(xn) - 0.33) < 0.12 and v > 0.3 else 0.0
                rim = -0.25 if abs(xn) > 0.84 or v < 0.06 else 0.0
                b = min(0.999, max(0.0, 0.52 - 0.3 * xn + 0.1 * v + seam + rim + dim))
                zbuf[row][col] = zt + 0.03
                chars[row][col] = PS[int(b * NP)]
                colors[row][col] = pal[int(b * npal)]
        return

    uxr, uyt, uzt = _rot(fl.u, ca, sa, ct, st)
    vxr, vyt, vzt = _rot(fl.v, ca, sa, ct, st)
    axr, ayt, azt = _rot(fl.axis, ca, sa, ct, st)
    m11, m12, m21, m22 = uxr * Rx, vxr * Rx, -uyt * Ry, -vyt * Ry
    big = max(abs(m11), abs(m12), abs(m21), abs(m22))
    if big < 0.55:  
        c0, r0 = int(fx), int(fy)
        if 0 <= r0 < view_rows and 0 <= c0 < cols and zt > zbuf[r0][c0] and big > 0.05:
            zbuf[r0][c0] = zt
            chars[r0][c0] = "o"
            colors[r0][c0] = GREENS[-1]
        return
    det = m11 * m22 - m12 * m21
    thr = 0.55 * big  
    if abs(det) < thr:
        det = thr if det >= 0 else -thr
    inv = 1.0 / det
    ex, ey = math.hypot(m11, m12), math.hypot(m21, m22)

    back = azt < -0.08  
    bl = 0.20 * (axr * LX + ayt * LY + azt * LZ)
    kz = R * fl.cup * azt
    off = (fl.seed + t * 0.3 + (1.0 - min(g, 1.0)) * 2.5) * INV_2PI
    kind, cr, base, slope = fl.kind, fl.cr, fl.base, fl.slope
    reach, tone, cpal = fl.reach, fl.tone, fl.cpal
    ncp = len(cpal) if cpal else 1

    for row in range(max(0, int(fy - ey) - 1), min(view_rows, int(fy + ey) + 2)):
        sy = row + 0.5 - fy
        zrow, crow, clrow = zbuf[row], chars[row], colors[row]
        shy = -0.26 * sy / ey
        for col in range(max(0, int(fx - ex) - 1), min(cols, int(fx + ex) + 2)):
            sx = col + 0.5 - fx
            a = (m22 * sx - m12 * sy) * inv
            b2 = (m11 * sy - m21 * sx) * inv
            s2 = a * a + b2 * b2
            if s2 > 1.0:
                continue
            zc = zt + R * (a * uzt + b2 * vzt) + kz * (1.0 - s2)
            if zc <= zrow[col]:
                continue
            s = math.sqrt(s2)
            u01 = math.atan2(b2, a) * INV_2PI + off
            ti = int((u01 % 1.0) * NTAB)
            if ti >= NTAB:
                ti = NTAB - 1
            rch = reach[ti]
            if s > rch:
                continue
            sh = shy - 0.20 * sx / ex  
            if back:
                if s < 0.5:
                    b = 0.30 + sh + dim * 0.5
                    b = min(0.999, max(0.0, b))
                    ch, color = "%", GREENS[int(b * len(GREENS))]
                else:
                    b = min(0.999, max(0.0, 0.30 + sh + dim - (0.2 if s > rch - 0.10 else 0.0)))
                    ch, color = PS[int(b * NP)], pal[int(b * npal)]
            elif kind == ROSE:
                sw = (s * 2.4 - u01) % 1.0  
                b = base + sh + bl + dim
                if sw < 0.22:
                    b -= 0.30
                elif sw > 0.82:
                    b += 0.16
                if s < 0.14:
                    b -= 0.22
                elif s > rch - 0.10:
                    b -= 0.28
                b = min(0.999, max(0.0, b))
                ch, color = PS[int(b * NP)], pal[int(b * npal)]
            elif s < cr:  
                if kind == SUN:  
                    chk = (int(s * 9.0) + int((u01 % 1.0) * 23.0)) & 1
                    b = 0.30 + 0.38 * chk + 0.5 * sh + 0.5 * bl + 0.5 * dim
                    ch = "@" if chk else "o"
                else:
                    b = 0.55 + 1.5 * sh + dim
                    ch = "@" if s < cr * 0.55 else "o"
                b = min(0.999, max(0.0, b))
                color = cpal[int(b * ncp)]
            else:
                b = base + sh + tone[ti] + bl + dim + slope * (s - 0.5)
                if s > rch - 0.10:
                    b -= 0.25  
                b = min(0.999, max(0.0, b))
                ch, color = PS[int(b * NP)], pal[int(b * npal)]
            zrow[col] = zc
            crow[col] = ch
            clrow[col] = color


def render(scene, t, ang, cols, rows, view_rows, scale, hearts, petals, msg, hint):
    chars = [[" "] * cols for _ in range(rows)]
    colors = [[0] * cols for _ in range(rows)]
    zbuf = [[-1e9] * cols for _ in range(rows)]

    tilt = TILT + 0.035 * math.sin(t * 0.5)
    ca, sa = math.cos(ang), math.sin(ang)
    ct, st = math.cos(tilt), math.sin(tilt)
    sxs = scale * 2.0
    cx = cols / 2
    cy = 1 + (TOP_Y - PIVOT_Y) * scale
    cam = (ca, sa, ct, st, cx, cy, sxs, scale)

    def plot(col, row, z, ch, color):
        if 0 <= row < view_rows and 0 <= col < cols and z > zbuf[row][col]:
            zbuf[row][col] = z
            chars[row][col] = ch
            colors[row][col] = color

    def project(x, y, z):
        xr = x * ca - z * sa
        zr = x * sa + z * ca
        yp = y - PIVOT_Y
        yt = yp * ct - zr * st
        zt = yp * st + zr * ct
        f = CAM_DIST / (CAM_DIST - zt)
        return int(cx + xr * f * sxs), int(cy - yt * f * scale), zt

   
    for sx_, sy_, ph, spd in scene.stars:
        tw = math.sin(t * spd + ph)
        col, row = int(sx_ * cols), int(sy_ * view_rows)
        if tw > 0.93:
            plot(col, row, -80, "+", 252)
        elif tw > 0.5:
            plot(col, row, -80, "\u00b7", 247)
        elif tw > 0.0:
            plot(col, row, -80, "\u00b7", 240)
    for x, y, _, phase, color in hearts:
        col = int((x + 0.015 * math.sin(t * 1.2 + phase)) * cols) % cols
        plot(col, int(y * view_rows), -50, HEART, color)
    for x, y, _, phase, color in petals:
        col = int((x + 0.04 * math.sin(t * 0.9 + phase)) * cols) % cols
        plot(col, int(y * view_rows), -50, PETAL_CHARS[int(t * 2.2 + phase * 3) % 4], color)

    # --- the bouquet
    draw_core(cam, zbuf, chars, colors, view_rows, cols)
    for fl in scene.flowers:
        g = ease_out_back((t - fl.delay) / 1.1) if INTRO else 1.0
        if g > 0.02:
            raster_flower(fl, g, t, cam, zbuf, chars, colors, view_rows, cols)
    draw_points(scene.pts, cam, zbuf, chars, colors, view_rows, cols)
    draw_points(dynamic_points(t, scene.K), cam, zbuf, chars, colors, view_rows, cols)

 
    show = 1.0 if not INTRO else min(1.0, max(0.0, (t - 2.5) / 2.0))
    if show > 0:
        for i, (x, y, z, phase) in enumerate(scene.babies):
            if i / len(scene.babies) > show:
                break
            col, row, zt = project(x, y, z)
            star = math.sin(t * 2 + phase) > 0.6
            plot(col, row, zt + 0.02, "*" if star else "\u00b7", 231 if star else 255)
        for x, y, z, phase, speed in scene.sparkles:
            col, row, zt = project(x, y, z)
            tw = math.sin(t * speed + phase)
            if tw > 0.85:
                plot(col, row, zt, "*", 231)
            elif tw > 0.4:
                plot(col, row, zt, "+", 225)
            elif tw > 0.0:
                plot(col, row, zt, "\u00b7", 218)
        for rad, y0, omega, phase in scene.flies:
            for k, (chh, colr) in enumerate((("*", 229), ("+", 223), ("\u00b7", 218), ("\u00b7", 175))):
                a = phase + t * omega - k * 0.10 * (1 if omega > 0 else -1)
                yy = y0 + 0.08 * math.sin(t * 0.9 + phase)
                col, row, zt = project(rad * math.cos(a), yy, rad * math.sin(a))
                plot(col, row, zt + 0.1, chh, colr)


    shift = int(t * 8)
    if TO_NAME:
        label = "for " + TO_NAME
        st0 = max(0, (cols - len(label)) // 2)
        for i, ch in enumerate(label):
            if st0 + i < cols and ch != " ":
                chars[0][st0 + i] = ch
                colors[0][st0 + i] = MSG_COLORS[(i + shift) % len(MSG_COLORS)]
    if hint > 0 and cols >= 70:
        txt = "space pause  \u00b7  +/- spin  \u00b7  r reverse  \u00b7  n next  \u00b7  q quit"
        limit = cols - 1 if not TO_NAME else (cols - len(TO_NAME)) // 2 - 8  
        for i, ch in enumerate(txt):
            if ch != " " and i + 1 < limit:
                chars[0][i + 1] = ch
                colors[0][i + 1] = 240 if hint > 0.5 else 238

    lines, lo, hi = msg
    n_total = sum(len(s) for s in lines)
    typing = lo == 0 and hi < n_total and int(t * 3) % 2 == 0
    idx = 0
    for li, line in enumerate(lines):
        r = view_rows + li
        if r >= rows - 1:
            break
        start = max(0, (cols - len(line)) // 2)
        for i, ch in enumerate(line):
            c = start + i
            if c < cols:
                if lo <= idx < hi and ch != " ":
                    chars[r][c] = ch
                    colors[r][c] = MSG_COLORS[(idx + shift) % len(MSG_COLORS)]
                elif idx == hi and typing:
                    chars[r][c] = "_"
                    colors[r][c] = 211
            idx += 1

    sig = SIGNATURE
    sstart = max(0, (cols - len(sig)) // 2)
    pulse = 238 + int(2 * (0.5 + 0.5 * math.sin(t * 1.5)))
    for i, ch in enumerate(sig):
        if sstart + i < cols:
            chars[rows - 1][sstart + i] = ch
            colors[rows - 1][sstart + i] = pulse

   
    out_lines = []
    for r in range(rows):
        rc, rcol = chars[r], colors[r]
        last = -1
        parts = []
        for c in range(cols):
            ch = rc[c]
            if ch != " " and rcol[c] != last:
                last = rcol[c]
                parts.append("\033[38;5;%dm" % last)
            parts.append(ch)
        out_lines.append("".join(parts))
    return "\033[H" + "\n".join(out_lines) + RESET



def update_particles(hearts, petals, dt):
    while len(hearts) < NUM_HEARTS:
        hearts.append([random.random(), random.uniform(0.0, 1.25), random.uniform(0.03, 0.08),
                       random.uniform(0, 6.28), random.choice(HEART_COLORS)])
    while len(petals) < NUM_PETALS:
        petals.append([random.random(), random.uniform(0.0, 1.25), random.uniform(0.05, 0.11),
                       random.uniform(0, 6.28), random.choice(PETAL_COLORS)])
    for group in (hearts, petals):
        for h in group:
            h[1] -= h[2] * dt
            if h[1] < 0:
                h[0], h[1] = random.random(), 1.0
                h[4] = random.choice(HEART_COLORS if group is hearts else PETAL_COLORS)


def msg_phase(n, tt):
    """Which characters [lo, hi) of a message are visible tt seconds after it starts typing."""
    type_d = n / TYPE_CPS
    hold = 2.6 + 0.03 * n
    erase_d = 0.9
    if tt < 0:
        return 0, 0, False
    if tt < type_d:
        return 0, int(tt * TYPE_CPS), False
    if tt < type_d + hold:
        return 0, n, False
    if tt < type_d + hold + erase_d:
        return int((tt - type_d - hold) / erase_d * n), n, False
    return n, n, tt > type_d + hold + erase_d + 0.5


class Keys:
    """Tiny non-blocking key reader (Windows + macOS/Linux). Quietly does nothing if there's no terminal."""

    def __init__(self):
        self.mode = None
        self.fd = None
        self.old = None

    def __enter__(self):
        try:
            if sys.stdin.isatty():
                if os.name == "nt":
                    import msvcrt  # noqa: F401
                    self.mode = "nt"
                else:
                    import termios
                    import tty
                    self.fd = sys.stdin.fileno()
                    self.old = termios.tcgetattr(self.fd)
                    tty.setcbreak(self.fd)
                    self.mode = "posix"
        except Exception:
            self.mode = None
        return self

    def __exit__(self, *exc):
        if self.mode == "posix":
            try:
                import termios
                termios.tcsetattr(self.fd, termios.TCSADRAIN, self.old)
            except Exception:
                pass
        return False

    def poll(self):
        out = []
        try:
            if self.mode == "nt":
                import msvcrt
                while msvcrt.kbhit():
                    ch = msvcrt.getwch()
                    if ch in ("\x00", "\xe0"):
                        msvcrt.getwch()
                    else:
                        out.append(ch)
            elif self.mode == "posix":
                import select
                while select.select([self.fd], [], [], 0)[0]:
                    data = os.read(self.fd, 64)
                    if not data:
                        break
                    out.extend(data.decode("utf-8", "ignore"))
        except Exception:
            pass
        return out



def main():
    """Run the bouquet animation and restore terminal state on exit."""
    if os.name == "nt":
        os.system("")  
    try:
        sys.stdout.reconfigure(encoding="utf-8")
    except (AttributeError, OSError):
        pass

    scene, scene_density = None, None
    hearts, petals = [], []
    wrap_cache = {}
    ang, spin_mul, spin_on = 0.0, 1.0, True
    msg_i, msg_t0 = 0, (0.9 if INTRO else 0.3)
    previous_size = None

    sys.stdout.write("\033[?1049h\033[?25l\033[2J\033[H")  
    sys.stdout.flush()
    start = last = time.perf_counter()

    try:
        with Keys() as keys:
            while True:
                frame_start = time.perf_counter()
                dt = min(0.1, max(0.0, frame_start - last))
                last = frame_start
                t = frame_start - start

                for k in keys.poll():
                    if k in ("q", "Q", "\x03"):
                        raise KeyboardInterrupt
                    elif k == " ":
                        spin_on = not spin_on
                    elif k in ("+", "="):
                        spin_mul = min(6.0, spin_mul * 1.25)
                    elif k in ("-", "_"):
                        spin_mul = max(0.1, spin_mul / 1.25)
                    elif k in ("r", "R"):
                        spin_mul = -spin_mul
                    elif k in ("n", "N"):
                        msg_i, msg_t0 = (msg_i + 1) % len(MESSAGES), t

                try:
                    terminal = shutil.get_terminal_size((80, 30))
                    cols, rows = max(20, terminal.columns - 1), max(12, terminal.lines - 1)
                except OSError:
                    cols, rows = 79, 29

                if (cols, rows) != previous_size:
                    sys.stdout.write("\033[2J\033[H")
                    previous_size = (cols, rows)
                    wrap_cache.clear()
                if cols not in wrap_cache:
                    width = max(12, cols - 4)
                    wrap_cache[cols] = [textwrap.wrap(m, width=width) or [""] for m in MESSAGES]
                wrapped = wrap_cache[cols]
                msg_rows = min(3, max(len(w) for w in wrapped))
                view_rows, scale = layout(cols, rows, msg_rows)

                density = round(max(0.6, min(1.6, scale / 24.0)) * 4) / 4
                if scene is None or density != scene_density:
                    scene, scene_density = build_scene(density), density

                if spin_on:
                    ang += SPIN_SPEED * spin_mul * dt
                update_particles(hearts, petals, dt)

                lines = wrapped[msg_i][:3]
                n_total = sum(len(s) for s in lines)
                lo, hi, done = msg_phase(n_total, t - msg_t0)
                if done:
                    msg_i, msg_t0 = (msg_i + 1) % len(MESSAGES), t
                hint = max(0.0, min(1.0, (11.0 - t) / 2.0))

                frame = render(scene, t, ang, cols, rows, view_rows, scale, hearts, petals,
                               (lines, lo, hi), hint)
                sys.stdout.write(frame)
                sys.stdout.flush()

                delay = (1.0 / FPS) - (time.perf_counter() - frame_start)
                if delay > 0:
                    time.sleep(delay)

    except KeyboardInterrupt:
        pass
    finally:
      
        sys.stdout.write(RESET + "\033[?25h\033[?1049l")
        sys.stdout.flush()
        print("\033[38;5;205m" + HEART + "\033[0m  thanks for watching it bloom")


if __name__ == "__main__":
    main()
