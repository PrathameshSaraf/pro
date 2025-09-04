# pro



class LiveRoomScreen extends StatefulWidget {
  @override
  State<LiveRoomScreen> createState() => _LiveRoomScreenState();
}

class _LiveRoomScreenState extends State<LiveRoomScreen> {
  // ---- Theme & constants ----
  static const Color kBg = Color(0xFFAF1D18);
  static const double kPad = 10;
  static const String kHostAvatar =
      'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTA-m4D7gaOaHMGxxheIp_xF_OSzrba6G7MIA&s';
  static const String kFlagIn = 'https://flagcdn.com/w20/in.png';
  static const String kSmallAvatar =
      'https://i.pinimg.com/736x/6b/aa/98/6baa98cc1c3f4d76e989701746e322dd.jpg';
  static const String kBanner =
      'https://wallpapers.com/images/featured/heroine-b9ste23c1zfuxnbz.jpg';

  // Use a bed icon PNG **with transparent background** for proper tinting:
  static const String kBedPngTransparent =
      'https://upload.wikimedia.org/wikipedia/commons/thumb/8/85/Font_Awesome_5_solid_bed.svg/1024px-Font_Awesome_5_solid_bed.svg.png';
  // ^ This URL is SVG rendered as PNG by Wikimedia; still has transparent bg in most sizes.
  // If you face issues, host your own transparent PNG, or use an SVG with flutter_svg.

  @override
  Widget build(BuildContext context) {
    return Scaffold(

      body: SafeArea(
        child: SingleChildScrollView(
          child: Column(
            crossAxisAlignment: CrossAxisAlignment.start,
            children: [
              Container(
                color: kBg,
                child: Column(
                  mainAxisSize: MainAxisSize.min,
                  crossAxisAlignment: CrossAxisAlignment.start,
                  children: [
                    5.verticalSpace,
                    Container(
                      color: kBg,
                      child: Row(
                        children: [
                          // Profile pill
                          Container(
                            height: 40,
                            padding:
                            const EdgeInsets.symmetric(horizontal: 3, vertical: 3),
                            decoration: BoxDecoration(
                              color: Colors.red.shade300,
                              borderRadius: BorderRadius.circular(30),
                            ),
                            child: Row(
                              mainAxisSize: MainAxisSize.min,
                              children: [
                                const CircleAvatar(
                                  radius: 15,
                                  backgroundImage: NetworkImage(kHostAvatar),
                                ),
                                const SizedBox(width: 8),
                                Column(
                                  crossAxisAlignment: CrossAxisAlignment.start,
                                  mainAxisAlignment: MainAxisAlignment.center,
                                  children: const [
                                    _FlagAndName(),
                                    Text(
                                      'ID: 6736373839',
                                      style: TextStyle(
                                        color: Colors.white,
                                        fontSize: 10,
                                      ),
                                    ),
                                  ],
                                ),
                                const SizedBox(width: 10),
                                Container(
                                  padding: const EdgeInsets.symmetric(
                                      horizontal: 16, vertical: 5),
                                  decoration: BoxDecoration(
                                    color: Color(0xFFac1214),
                                    borderRadius: BorderRadius.circular(20),
                                  ),
                                  child: const Icon(
                                    Icons.add_circle,
                                    color: Colors.white,
                                    size: 22,
                                  ),
                                ),
                              ],
                            ),
                          ),
                          const Spacer(),
                          // Right cluster
                          Row(
                            mainAxisSize: MainAxisSize.min,
                            children: [
                              const _MiniAvatar(url: kSmallAvatar),
                              const _MiniAvatar(url: kSmallAvatar),
                              Container(
                                margin: const EdgeInsets.only(right: 8),
                                width: 30,
                                height: 30,
                                decoration: BoxDecoration(
                                  color: Color(0xffcd6866),
                                  shape: BoxShape.circle,
                                ),
                                child: const Center(
                                  child: Text(
                                    '19',
                                    style: TextStyle(
                                      color: Colors.white,
                                      fontWeight: FontWeight.bold,
                                      fontSize: 14,
                                    ),
                                  ),
                                ),
                              ),
                              GestureDetector(
                                onTap: () {
                                  // TODO: close action
                                },
                                child: Container(
                                  width: 30,
                                  height: 30,
                                  decoration: const BoxDecoration(
                                    color: Colors.white24,
                                    shape: BoxShape.circle,
                                  ),
                                  child: const Icon(
                                    Icons.close,
                                    color: Colors.white,
                                    size: 20,
                                  ),
                                ),
                              ),
                            ],
                          ),
                        ],
                      ),
                    ),
                    10.verticalSpace,
                    // Make a wish
                    Container(
                      height: 50,
                      width: 100,
                      decoration: BoxDecoration(
                        color: Color(0xffcd6866),
                        borderRadius: BorderRadius.circular(5),
                      ),
                      child: const Row(
                        mainAxisAlignment: MainAxisAlignment.center,
                        children: [
                          Icon(Icons.auto_fix_high, color: Colors.white, size: 20),
                          SizedBox(width: 5),
                          Flexible(
                            child: Text(
                              'Make a\nWish',
                              style: TextStyle(
                                color: Colors.white,
                                fontWeight: FontWeight.bold,
                                fontSize: 12,
                              ),
                              textAlign: TextAlign.center,
                            ),
                          ),
                        ],
                      ),
                    ),

                    Align(
                      alignment: Alignment.centerRight,
                      child: Container(
                        height: 35,
                        padding: const EdgeInsets.symmetric(horizontal: 8),
                        decoration: BoxDecoration(
                          color:Color(0xffcd6866),
                          borderRadius: BorderRadius.circular(5),
                        ),
                        child: const Row(
                          mainAxisSize: MainAxisSize.min,
                          children: [
                            Icon(Icons.person_add_alt_1,
                                color: Colors.white, size: 18),
                            SizedBox(width: 5),
                            Text(
                              'Invite your friends',
                              style: TextStyle(
                                color: Colors.white,
                                fontWeight: FontWeight.bold,
                                fontSize: 14,
                              ),
                            ),
                          ],
                        ),
                      ),
                    ),
                    5.verticalSpace,
                  ],
                ),
              ),


              // Banner
              ClipRRect(
                borderRadius: BorderRadius.circular(10),
                child: Container(
                  height: 180,
                  padding: EdgeInsets.all(5),
                  width: double.infinity,
                  decoration: const BoxDecoration(color: Colors.white24),
                  child: Image.network(
                    kBanner,
                    fit: BoxFit.cover,
                    errorBuilder: (_, __, ___) => const ColoredBox(
                      color: Colors.white24,
                      child: Center(
                        child: Icon(Icons.image_not_supported,
                            color: Colors.white70),
                      ),
                    ),
                  ),
                ),
              ),


              // Seats grid
              GridView.builder(
                shrinkWrap: true,
                physics: const NeverScrollableScrollPhysics(),
                gridDelegate: const SliverGridDelegateWithFixedCrossAxisCount(
                  crossAxisCount: 3,
                  mainAxisSpacing: 1,
                  crossAxisSpacing: 1,
                  childAspectRatio: 1.1,
                ),
                itemCount: 6,
                itemBuilder: (context, index) {
                  final bool isOccupied = index == 0; // sample occupied seat
                  return SeatTile(
                    index: index,
                    occupied: isOccupied,
                    bgColor:
                    isOccupied || index==2 || index==4? Color(0xffd64041) : Color(0xFFe0bebf),
                    borderColor: Colors.red.shade300,
                    // White icon on transparent PNG:
                    emptyIcon: TintableNetworkImage(
                      imageUrl: kBedPngTransparent,
                      // If your image is truly transparent, this will make only the icon white:
                      color: Colors.white,
                      width: 40,
                      height: 40,
                    ),
                  );
                },
              ),

              Container(
                height: 400,
                width: double.infinity,
                decoration: BoxDecoration(
                  gradient: const LinearGradient(
                    begin: Alignment.topCenter,
                    end: Alignment.bottomCenter,
                    colors: [Color(0xFFF5AE70), Color(0xFFEC9963)], // new gradient
                  ),
                  borderRadius: BorderRadius.circular(1),
                ),
                child: Stack(
                  children: [
                    // ---------------- TOP LEFT: 2 round couch buttons (STATIC) ----------------
                    Positioned(
                      top: 12,
                      left: 12,
                      child: Row(
                        children: [
                          Stack(
                            clipBehavior: Clip.none,
                            children: [
                              Container(
                                width: 40,
                                height: 40,
                                decoration: const BoxDecoration(
                                  color: Color(0xFFD43D3D),
                                  shape: BoxShape.circle,
                                ),
                                child: const Icon(Icons.weekend_rounded,
                                    color: Colors.white, size: 26),
                              ),
                              Positioned(
                                right: -2,
                                top: -2,
                                child: Container(
                                  width: 18,
                                  height: 18,
                                  decoration: BoxDecoration(
                                    color: Colors.white,
                                    borderRadius: BorderRadius.circular(9),
                                    border: Border.all(color: Color(0xFFD43D3D), width: 2),
                                  ),
                                  alignment: Alignment.center,
                                  child: const Text('1',
                                      style: TextStyle(
                                          fontSize: 10,
                                          fontWeight: FontWeight.w700,
                                          color: Color(0xFFD43D3D))),
                                ),
                              ),
                            ],
                          ),
                          5.horizontalSpace,
                          Container(
                            width: 40,
                            height: 40,
                            decoration: const BoxDecoration(
                              color: Color(0xFFD43D3D),
                              shape: BoxShape.circle,
                            ),
                            child: const Icon(Icons.weekend_rounded,
                                color: Colors.white, size: 26),
                          ),
                        ],
                      ),
                    ),

                    // ---------------- TOP RIGHT: avatars + blue couch (STATIC) ----------------
                    Positioned(
                      top: 10,
                      right: 12,
                      child: Row(
                        children: [
                          const CircleAvatar(
                            radius: 10,
                            backgroundImage: NetworkImage(
                                'https://images.unsplash.com/photo-1527980965255-d3b416303d12?w=200'),
                          ),
                          const CircleAvatar(
                            radius: 10,
                            backgroundImage: NetworkImage(
                                'https://images.unsplash.com/photo-1507003211169-0a1dd7228f2d?w=200'),
                          ),
                          const CircleAvatar(
                            radius: 10,
                            backgroundImage: NetworkImage(
                                'https://images.unsplash.com/photo-1544005313-94ddf0286df2?w=200'),
                          ),
                          const SizedBox(width: 10),
                          Container(
                            width: 40,
                            height: 40,
                            decoration: const BoxDecoration(
                              color: Color(0xFF2E6DBB),
                              shape: BoxShape.circle,
                            ),
                            child: const Icon(Icons.weekend_rounded,
                                color: Colors.white, size: 24),
                          ),
                        ],
                      ),
                    ),

                    // ---------------- LEFT RAIL (STATIC) ----------------
                    Positioned(
                      top: 80,
                      left: 10,
                      child: Container(
                        width: 30,
                        height: 80,
                        decoration: BoxDecoration(
                          color: Colors.white.withOpacity(0.35),
                          borderRadius: BorderRadius.circular(24),
                        ),
                        alignment: Alignment.center,
                        child: RotatedBox(
                          quarterTurns: 3,
                          child: Text(
                            'Room',
                            style: TextStyle(
                              color: Colors.white.withOpacity(0.95),
                              fontWeight: FontWeight.w700,
                              letterSpacing: 0.5,
                            ),
                          ),
                        ),
                      ),
                    ),
                    Positioned(
                      top: 170,
                      left: 10,
                      child: Container(
                        width: 30,
                        height: 80,
                        decoration: BoxDecoration(
                          color: Colors.white.withOpacity(0.35),
                          borderRadius: BorderRadius.circular(24),
                        ),
                        alignment: Alignment.center,
                        child: RotatedBox(
                          quarterTurns: 3,
                          child: Text(
                            'Chat',
                            style: TextStyle(
                              color: Colors.white.withOpacity(0.95),
                              fontWeight: FontWeight.w700,
                              letterSpacing: 0.5,
                            ),
                          ),
                        ),
                      ),
                    ),



                    // ---------------- RIGHT AVATARS (STATIC) ----------------
                    Positioned(
                      top: 220,
                      right: 10,
                      child: Column(
                        children: const [
                          CircleAvatar(
                            radius: 14,
                            backgroundImage: NetworkImage(
                                'https://images.unsplash.com/photo-1544005313-94ddf0286df2?w=200'),
                          ),
                          SizedBox(height: 5),
                          CircleAvatar(
                            radius: 14,
                            backgroundImage: NetworkImage(
                                'https://images.unsplash.com/photo-1500648767791-00dcc994a43e?w=200'),
                          ),
                          SizedBox(height: 8),
                          Icon(Icons.keyboard_arrow_down_rounded,
                              color: Colors.white, size: 26),
                        ],
                      ),
                    ),

                    // ---------------- MESSAGES: SCROLLABLE, FIXED HEIGHT = 200 ----------------
                    Positioned(
                      top: 70,
                      left: 60,
                      right: 60,
                      child: SizedBox(
                        height: 240,
                        child: SingleChildScrollView(
                          physics: const BouncingScrollPhysics(),
                          child: Column(
                            mainAxisAlignment: MainAxisAlignment.start,
                            crossAxisAlignment: CrossAxisAlignment.start,
                            children: [
                              Container(
                                padding: const EdgeInsets.fromLTRB(12, 10, 12, 8),
                                decoration: BoxDecoration(
                                  color: Colors.white.withOpacity(0.22),
                                  borderRadius: BorderRadius.circular(10),
                                  border: Border.all(color: const Color(0xFFC94B3E), width: 1.5),
                                ),
                                child: Column(
                                  crossAxisAlignment: CrossAxisAlignment.start,
                                  children: const [
                                    Text('Any storyline',
                                        style: TextStyle(
                                            color: Colors.white70,
                                            fontWeight: FontWeight.w600,
                                            fontSize: 14)),
                                    SizedBox(height: 6),
                                    Text('Go and see  »',
                                        style: TextStyle(
                                            color: Colors.white, fontWeight: FontWeight.w700)),
                                  ],
                                ),
                              ),
                              const SizedBox(height: 10),
                              Container(
                                padding: const EdgeInsets.fromLTRB(12, 10, 12, 8),
                                decoration: BoxDecoration(
                                  color: Colors.white.withOpacity(0.22),
                                  borderRadius: BorderRadius.circular(10),
                                  border: Border.all(color: const Color(0xFFC94B3E), width: 1.5),
                                ),
                                child: Column(
                                  crossAxisAlignment: CrossAxisAlignment.start,
                                  children: const [
                                    Text(
                                      'Madma-o1 won 2,09098 diamonds in ocean hunt.',
                                      style: TextStyle(
                                        color: Colors.white70,
                                        fontWeight: FontWeight.w600,
                                        fontSize: 14,
                                      ),
                                    ),
                                    SizedBox(height: 6),
                                    Text('Ocean Hunt  »',
                                        style: TextStyle(
                                            color: Colors.white, fontWeight: FontWeight.w700)),
                                  ],
                                ),
                              ),
                              // repeatable message bubble
                              for (final text in [
                                'Rajiv1265',
                                'Vivek the king',
                                'I am rider',
                              ])
                                Padding(
                                  padding: const EdgeInsets.only(bottom: 5.0, top: 5.0),
                                  child: Container(
                                    padding: const EdgeInsets.symmetric(
                                        horizontal: 10, vertical: 7),
                                    decoration: BoxDecoration(
                                      color: const Color(0xFFB1111A),
                                      borderRadius: BorderRadius.circular(26),
                                    ),
                                    child: Row(
                                      children: [
                                        Text(text,
                                            style: const TextStyle(
                                                color: Colors.white,
                                                fontWeight: FontWeight.w700,
                                                fontSize: 12)),
                                        20.horizontalSpace,
                                        const Opacity(
                                          opacity: 0.75,
                                          child: Text('Joined',
                                              style: TextStyle(
                                                  color: Colors.white,
                                                  fontWeight: FontWeight.w600,
                                                  fontSize: 12)),
                                        ),
                                      ],
                                    ),
                                  ),
                                ),
                            ],
                          ),
                        ),
                      ),
                    ),

                    // ---------------- BOTTOM ACTION BAR (STATIC) ----------------
                    Positioned(
                      left: 18,
                      right: 18,
                      bottom: 16,
                      child: Row(
                        mainAxisAlignment: MainAxisAlignment.spaceBetween,
                        children: [
                          Row(
                            children: [
                              Container(
                                width: 46,
                                height: 46,
                                decoration: BoxDecoration(
                                  color: Colors.white.withOpacity(0.35),
                                  shape: BoxShape.circle,
                                ),
                                child: const Icon(Icons.chat_bubble_rounded,
                                    color: Colors.white, size: 22),
                              ),
                              const SizedBox(width: 12),
                              Container(
                                width: 46,
                                height: 46,
                                decoration: BoxDecoration(
                                  color: Colors.white.withOpacity(0.35),
                                  shape: BoxShape.circle,
                                ),
                                child: const Icon(Icons.mic_none_rounded,
                                    color: Colors.white, size: 22),
                              ),
                            ],
                          ),
                          Row(
                            children: [
                              Container(
                                width: 46,
                                height: 46,
                                decoration: BoxDecoration(
                                  color: Colors.white.withOpacity(0.35),
                                  shape: BoxShape.circle,
                                ),
                                child: const Icon(Icons.grid_view_rounded,
                                    color: Colors.white, size: 22),
                              ),
                              const SizedBox(width: 12),
                              Container(
                                width: 46,
                                height: 46,
                                decoration: BoxDecoration(
                                  color: Colors.white.withOpacity(0.35),
                                  shape: BoxShape.circle,
                                ),
                                child: const Icon(Icons.search_rounded,
                                    color: Colors.white, size: 22),
                              ),
                              const SizedBox(width: 12),
                              Container(
                                width: 46,
                                height: 46,
                                decoration: BoxDecoration(
                                  color: Colors.white.withOpacity(0.35),
                                  shape: BoxShape.circle,
                                ),
                                child: const Icon(Icons.weekend_rounded,
                                    color: Colors.white, size: 22),
                              ),
                              const SizedBox(width: 12),
                              Container(
                                width: 46,
                                height: 46,
                                decoration: BoxDecoration(
                                  color: Colors.white.withOpacity(0.35),
                                  shape: BoxShape.circle,
                                ),
                                child: const Icon(Icons.card_giftcard_rounded,
                                    color: Colors.white, size: 22),
                              ),
                            ],
                          ),
                        ],
                      ),
                    ),
                  ],
                ),
              )


            ],
          ),
        ),
      ),
    );
  }
}

// --- Small widgets ---

class _FlagAndName extends StatelessWidget {
  const _FlagAndName();

  @override
  Widget build(BuildContext context) {
    return Row(
      children: const [
        Image(
          image: NetworkImage(_LiveRoomScreenState.kFlagIn),
          width: 15,
          height: 14,
        ),
        SizedBox(width: 3),
        Text(
          'I am racer',
          style: TextStyle(
            color: Colors.white,
            fontWeight: FontWeight.bold,
            fontSize: 12,
          ),
        ),
      ],
    );
  }
}

class _MiniAvatar extends StatelessWidget {
  final String url;
  const _MiniAvatar({required this.url});

  @override
  Widget build(BuildContext context) {
    return Container(
      margin: const EdgeInsets.only(right: 3),
      child: CircleAvatar(
        radius: 10,
        backgroundImage: NetworkImage(url),
        backgroundColor: Colors.grey.shade300,
      ),
    );
  }
}

// --- Seat tile ---

class SeatTile extends StatelessWidget {
  final int index;
  final bool occupied;
  final Color bgColor;
  final Color borderColor;
  final Widget emptyIcon;

  const SeatTile({
    Key? key,
    required this.index,
    required this.occupied,
    required this.bgColor,
    required this.borderColor,
    required this.emptyIcon,
  }) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return Container(
      decoration: BoxDecoration(
        color: bgColor,
        borderRadius: BorderRadius.circular(2),
        border: Border.all(color: borderColor, width: 2),
      ),
      child: Stack(
        children: [
          // Seat number
          Positioned(
            top: 4,
            left: 4,
            child: CircleAvatar(
              radius: 8,
              backgroundColor: Colors.white,
              child: Text(
                '${index + 1}',
                style: TextStyle(
                  color: bgColor,
                  fontWeight: FontWeight.bold,
                  fontSize: 11,
                ),
              ),
            ),
          ),
          // Content
          Center(
            child: occupied
                ? Column(
              mainAxisAlignment: MainAxisAlignment.center,
              children: const [
                CircleAvatar(
                  radius: 20,
                  backgroundImage: NetworkImage(
                    'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTp3Ynotz5HJ_hcTtymP2AVfAz6-UICZFghZw&s',
                  ),
                ),
                SizedBox(height: 4),
                Text(
                  'John Doe',
                  style: TextStyle(
                    color: Colors.white,
                    fontSize: 10,
                    fontWeight: FontWeight.bold,
                  ),
                ),
              ],
            )
                : emptyIcon,
          ),
        ],
      ),
    );
  }
}

/// Tints only non-transparent pixels of a (preferably transparent-background) image.
/// If your source has a solid background, use a proper transparent PNG or an SVG.
class TintableNetworkImage extends StatelessWidget {
  final String imageUrl;
  final Color color;
  final double? width;
  final double? height;
  final BoxFit fit;

  const TintableNetworkImage({
    Key? key,
    required this.imageUrl,
    required this.color,
    this.width,
    this.height,
    this.fit = BoxFit.contain,
  }) : super(key: key);

  @override
  Widget build(BuildContext context) {
    return ColorFiltered(
      // srcIn keeps the image alpha while replacing RGB with `color`
      colorFilter: ColorFilter.mode(color, BlendMode.srcIn),
      child: Image.network(
        imageUrl,
        width: width,
        height: height,
        fit: fit,
        // These two lines also work, but ColorFiltered is clearer:
        // color: color,
        // colorBlendMode: BlendMode.srcIn,
        errorBuilder: (context, error, stackTrace) {
          return Icon(Icons.bed, size: width ?? 40, color: color);
        },
      ),
    );
  }
}
