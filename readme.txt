Glade�p�Ђт��̐݌v�֘A�t�@�C��(2017/1/24:akita11)

�X�^���_�[�h�Z���̎g����
1. File->New Lib�Ń��C�u�������쐬�B���̂Ƃ��ATechnology��hibikino.tch���w�肷��i�����Ń��C����`�Ȃǂ��ݒ肳���j
2. File->Import->Import GDS2�ŁAstdcell_v2.gds���w�肷��B���̂Ƃ��ǂݍ��ރ��C�u�������A1.�ō쐬�������C�u�����ɐݒ肷��B�܂���File->Open Library�ŁA�����ɂ��� StdCell_v2���w�肷��B
3. �X�^�Z�������̃��C�u�����ɓǂݍ��܂��̂ŁA������g���ĐV������H(Cellview)������

DRC�t�@�C���̎g����
Verify->DRC->Run DRC (Shift+D)�ŁA"hibikino-drc.py" ���w�肵��DRC��������B
�G���[�������Verify->DRC->View DRC Errors�Ŋm�F�ł���

��H���o�̎g����
Verify->Extract->RunLVE�ŁA"hibikino-ext.py"���w�肷��ƁA���̃Z���ɑ΂���extracted�Ƃ����r���[���ł���B�E����"Net Browser"�ɁA�l�b�g��������A�ǂꂩ��I������ƁA���̃l�b�g�ɑΉ�����I�u�W�F�N�g���n�C���C�g�����B�Ȃ����C�A�E�g�ŁAML1/ML2/POL�ɓ������C���ŏ�����������i������̐���_���Ώې}�`�̒��ɂ��邱�Ɓj���A���̃l�b�g�̃l�b�g���ɂȂ�B�l�b�g���X�g�t�@�C���̏o�͂́AFile->Export->Export CDL�ŁA�i�قځjspice�`���ŏo�͂ł���B

��H�}����
�EMOS��StdCell_v2���̃Z��nch/pch���g���B
�E���o�͂́ACreate->Pin�Ńs���Ƃ��āA���̂����č쐬�B
�EVDD/GND���́Abasic���C�u��������vdd/gnd���g���B�܂��͓��o�͂Ɠ������s���Ƃ��č쐬����B
�E�����̒[�q�i�Ԃ��l�p�j��Wire�Ō��ԁB
�Ȃ�Wire�͍ŏ��̓l�b�g�������Ă��Ȃ����ACheck Cellview����ƃl�b�g�������B
�Ȃ����Ă���͂��Ȃ̂ɂȂ����Ă��Ȃ��i�����Ă���j�A�Ƃ����G���[���o�邱�Ƃ����邪�A�ēxCheck Cellview����Ǝ��邱�Ƃ�����i�䋓���j�B
�[�_��wire��2��ڂ��N���b�N����ƁAwire�z�����I���̂ŁA����łȂ����Ă��邩�͔��f�ł���i�[�_��ŃN���b�N���Ȃ���wire�z���������j�B
File->Export��Export CDL�Łi�قځjspice�`���̃l�b�g���X�g���o�͂ł���B

LVS�̂�����
1.���C�A�E�g("layout")���J���A���̎菇�ŉ�H���o�B"extracted"�r���[�����������B
2."extracted"�r���[���J���A��������Verify->LVS->Run LVS��LVS�����s�B��ʂ̉E���Ł��ŉ�H�}����export�����l�b�g���X�g(CDL�`��)���w�肷��B
3.LVS�����{�����B�Ȃ�MOS�g�����W�X�^�̃T�C�Y�̕s��v�͌��o����Ȃ��͗l�i�ڍז��m�F�j�B

Glade���상��
DisplayOption->Miscellaneous��Always pop up option dialog���͂����ƁAMove�Ȃǂ̂��тɃI�v�V������ʂ��\������Ȃ��iF3�œK�X�\���ł���j

